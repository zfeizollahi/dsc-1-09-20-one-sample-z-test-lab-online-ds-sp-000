
# One-Sample z-test - Lab

## Introduction
In this lab you'll perform a few quick tests to help you better understand how hypothesis testing works.

## Objectives
You will be able to:
* Understand and explain use cases for a one-sample z-test
* Set up null and alternative hypotheses
* Calculate z-statistic using z-tables and CDF functions
* Calculate and interpret p-value for significance of results

## Exercise 1
A fast food chain claims that the mean time to order food at their restaurants is 60 seconds, with a standard deviation of 30 seconds. You decide to take this claim to the test and go to one of the restaurants to observe actual waiting times. You take a sample of 36 customers and find that the mean order time was 75 seconds. Does this finding prove enough evidence to contradict the fast food chain's claim of fast service?

Follow the 5 steps shown in previous lesson and use $\alpha$ = 0.05. 

### State you null and alternative hypotheses
Null Hypothesis: the observed order time is no different than the claim of 60 second wait time.
Althernative Hypothesis: the observed order time is greater than the claim of 60 seconds wait time.


```python
# Your solution here
import scipy.stats as stats
from math import sqrt
import numpy as np

z_stat = (75 - 60) / ( 30 / sqrt(36) )
p = stats.norm.cdf(z_stat)
print(z_stat)
print(1 - p)
# (p = 0.0013498980316301035, z = 3.0)
```

    3.0
    0.0013498980316301035


### Interpret the results in terms of the p-value

P-value is less than 0.05, so we can reject the null hypthosis, 
wait times are significantly longer than the claim of 60 seconds.

## Exercise 2

25 students complete a preparation program for taking the SAT test.  Here are the SAT scores from the 25 students who completed  program:

``
434 694 457 534 720 400 484 478 610 641 425 636 454 
514 563 370 499 640 501 625 612 471 598 509 531
``

We know that the population average for SAT scores is 500 with a standard deviation of 100.

Are our 25 students’ SAT scores significantly bigger than a population mean? 

*Note that the SAT preparation program claims that it will increase (and not decrease) the SAT score.  So, you can conduct a one-directional test. (alpha = .05).*

### State your hypotheses 
Null: there is no difference between SAT scores of students who prep vs. those who don't
Alternative: there is a significantly higher SAT scores for students who prep vs. those who don't


```python
# Give your solution here 
sat = np.array([434, 694, 457, 534, 720, 400, 484, 478, 610, 641, 425, 636, 454, 
                514, 563, 370, 499, 640, 501, 625, 612, 471, 598, 509, 531])

z_stat = (sat.mean() - 500) / ( 100 / sqrt(len(sat)) )
p = stats.norm.cdf(z_stat)
print(sat.mean())
print(len(sat))
print(sat.std())
print(z_stat)
print( 1 - p)
# p = 0.03593031911292577, z = 1.8
```

    536.0
    25
    91.7121584087955
    1.8
    0.03593031911292577


### Interpret the results in terms of the p-value
We can reject the null hypothesis that there is no difference between students who
prep at a significance level of p=0.04 (alpha p<0.05)

## Summary

In this lesson, you conducted a couple of simple tests comparing sample and population means, in an attempt to reject our null hypotheses. This provides you with a strong foundation to move ahead with more advanced tests and approaches later on.
