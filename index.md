---
title       : Predicting Miles Per Gallon
subtitle    : Homework Assignment of Developing Data Products
author      : tucuxi
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
---

## Overview

**Fuel efficiency** is getting increasingly important for car buyers.

A popular measure for fuel efficiency is **Miles Per Gallon** (mpg).

Using R and Shiny, we build a **web application** for predicting mpg from basic
car specifications.

The presentation is organized as follows:

1. Data set
2. Linear model for predicting miles per gallon
3. Shiny application

--- 

## Data Set



We use the **mtcars** data set from the **datasets** package, which contains
data from Motor Trend US magazine for 32 cars. This will be the basis for the
linear model.

Column  | Variable    | Description
------- | ----------- | -------------------
1       | mpg         | Miles/(US) gallon
2       | cyl         | Number of cylinders
3       | disp        | Displacement (cu.in.)
4       | hp          | Gross horsepower
5       | drat        | Rear axle ratio
6       | wt          | Weight (lb/1000)
7       | qsec	      | 1/4 mile time
8       | vs	      | V/S
9       | am	      | Transmission (0 = automatic, 1 = manual)
10      | gear	      | Number of forward gears
11      | carb	      | Number of carburetors

---

## Linear Model for Predicting Miles Per Gallon

We build a **linear model** for mpg with two predictors:
weight (wt) and number of cylinders (cyl).


```
## 
## Call:
## lm(formula = mpg ~ wt + factor(cyl), data = mtcars)
## 
## Coefficients:
##  (Intercept)            wt  factor(cyl)6  factor(cyl)8  
##        33.99         -3.21         -4.26         -6.07
```

This model has **statistically significant P-values** (< 0.05) as shown below:


```r
summary(lm)$coefficients[, 4]
```

```
##  (Intercept)           wt factor(cyl)6 factor(cyl)8 
##    6.257e-17    2.130e-04    4.718e-03    9.992e-04
```

---

## Shiny Application

The web application built with [Shiny](http://shiny.rstudio.com)

* prompts the user for number of cylinders and weight,
* plots the linear model,
* predicts the mpg value for the given parameters, and
* highlights the predicted mpg value in the plot.

The prediction is done with the **predict()** function as shown in the
following example for a car with 6 cylinders and a weight of 3,500 lbs:


```r
predict(lm, data.frame(cyl = 6, wt = 3.5))
```

```
##     1 
## 18.52
```

Try out the application [here](http://tucuxi.shinyapps.io/data_products)!

<style>
strong {
  font-weight: bold;
}
</style>
