
<!-- README.md is generated from README.Rmd. Please edit that file -->

# syn <img src="man/figures/logo.png" align="right" height=140/>

[![Travis build
status](https://travis-ci.org/ropenscilabs/syn.svg?branch=master)](https://travis-ci.org/ropenscilabs/syn)[![AppVeyor
build
status](https://ci.appveyor.com/api/projects/status/github/ropenscilabs/syn?branch=master&svg=true)](https://ci.appveyor.com/project/ropenscilabs/syn)[![Coverage
status](https://codecov.io/gh/ropenscilabs/syn/branch/master/graph/badge.svg)](https://codecov.io/github/ropenscilabs/syn?branch=master)

`syn` is a **zero dependency** R package that lists synonyms and
antonyms.

There are two main functions:

  - `syn("great")` Returns synonyms of “great”
  - `ant("great")` Returns antonyms of “great”.

`syn` and `ant` take one word as input. To return synonyms for many
words, use the plural form: `syn`**s**, and `ant`**s**

  - `syns(c("great", "excellent")` Returns named list of synonyms of
    “great”, and “excellent”
  - `ants(c("great", "excellent")` Returns named list of antonyms of
    “great”, and “excellent”

## Example: Synonyms for “cool”

The `syn` function returns all synonyms for a given word:

Let’s look at synonyms for “cool”:

``` r
library(syn)

syn_cool <- syn("cool")

head(syn_cool)
#> [1] "abate"          "abnegation"     "above all that" "absolute zero" 
#> [5] "abstinence"     "ace-high"
tail(syn_cool)
#> [1] "withhold"       "without nerves" "wizard"         "wonderless"    
#> [5] "wonderlessness" "zealless"
```

Wow, there are a lot\! How many are there?

``` r
length(syn_cool)
#> [1] 618
```

Wow\! There are 618 synonyms for cool. That’s…unaffable, I guess.

You can also provide it a number of words to return with the `n_words`
argument, which will randomly select the number of words given

``` r
syn("awesome", 1)
#> [1] "astounding"
syn("awesome", 2)
#> [1] "boundless"       "high and mighty"
syn("awesome", 5)
#> [1] "cosmic"       "sublime"      "awful"        "time-honored"
#> [5] "venerable"
```

## Example: Creating a sentence

OK cool, let’s use these in a sentence, using the `glue` package. Which
of these better?

``` r

glue::glue("This is really cool!")
#> This is really cool!
glue::glue("This is really {syn('cool', 1)}!")
#> This is really stilly!
glue::glue("This is really {syn('cool', 10)}!")
#> This is really calm of mind!
#> This is really smooth!
#> This is really glowing!
#> This is really placid!
#> This is really gentle!
#> This is really soulless!
#> This is really suppressed!
#> This is really unresponding!
#> This is really Olympian!
#> This is really nonchalant!
```

## Using multiple words with `syns`

You can generate synonyms for multiple words with the `syns` function.
This takes a vector of words, returning a named list

``` r
syns_good_evil <- syns(c("good", "evil"))
str(syns_good_evil)
#> List of 2
#>  $ good: chr [1:667] "able to pay" "absolutely" "acceptable" "accomplished" ...
#>  $ evil: chr [1:365] "aberrant" "abnormal" "abominable" "abomination" ...
```

You can also provide `n_words` for `syns`, and it will return a random
selection of the words of that number.

``` r
syns(c("good", "evil"),
     n_words =  10)
#> $good
#>  [1] "valid"         "tender"        "undisguised"   "humanely"     
#>  [5] "advisable"     "favorable"     "clever"        "good-tasting" 
#>  [9] "word-for-word" "solid"        
#> 
#> $evil
#>  [1] "pest"           "besetment"      "poisonous"      "revolting"     
#>  [5] "cataclysm"      "dire"           "unpardonable"   "inexpiable sin"
#>  [9] "torment"        "spiteful"
```

## Example: Antonyms (under development)

To create antonyms, use `ant` and `ants`, which have the same inputs as
`syn`. However, at this stage, the number of antonyms available for use
by `ant` is small.

``` r
ant("good")
#> [1] "bad"  "evil"
ant("good",1)
#> [1] "bad"

ant("strong")
#> [1] "weak"
```

``` r
ants(c("good", "evil"))
#> $good
#> [1] "bad"  "evil"
#> 
#> $evil
#> [1] "good"

ants(c("good", "evil"), n_words = 5)
#> $good
#> [1] "evil" "bad" 
#> 
#> $evil
#> [1] "good"

ants(c("strong", "weak"))
#> $strong
#> [1] "weak"
#> 
#> $weak
#> [1] "strong"
```

## Code of Conduct

Please note that the ‘syn’ project is released with a [Contributor Code
of Conduct](CODE_OF_CONDUCT.md). By contributing to this project, you
agree to abide by its terms.
