---
title: Project Report for Coursera Statistical Inference Class
author: Balogun Stephen Taiye
date: system.date()
---

# Overview
 The project seeks to investigate the distribution of averages of 40 exponentials
and compare it with the Central Limit Theorem (*CLT*)

# Simulations
We are given a sample size (n) to be 40 and a formular $rexp(n, lambda)$ where:
        - $rexp$ is R exponential distribution
        - $n$ is the sample size
        - $lambda is the rate for the sample size (rate given as 0.2)
 
Using Bootstrap technique, we try to simulate the data to get several 1000 *means* 
of the data. The formular for the simulation is given as: 
        
```{r, "simulated data"}
B <- 1000   ##  number of times to simulate the data
n <- 40   ##   sample size
lambda <- 0.2   ## the given rate
simulate <- apply(matrix(sample(rexp(n, lambda), B*n, replace = TRUE),
                         n), 1, mean)
```
The formular given above samples the given data with replacement and draws 
sample size 40 1000 times, then find the mean of those 1000 samples

# Sample Mean versus the Theoretical Mean
 
The $theoretical mean$ of the *R* code `rexp(n, lamba)` is given as $1/lambda$.
The formular belows shows a plot that compares this *theoretical mean* with the 
*mean of our simulated data*.

```{r, "theoretical mean vs sample mean"}
hist(simulate)
abline(v = mean(simulate), lwd = 3, col = "blue")  ## shows the sample mean
abline (v = 1/lambda, lty = "dashed", lwd = 3)   ## shows the theoretical mean on the same plot
```

Rounding up the simulated data $mean$ 2 decimal places and comparing it with The
theoretical mean shows that the simulated mean approximates the theoretical mean(
        
```{r, "table simulated mean and theoretical mean"}
simulatedMean <- round(mean(simulate), 3)
theoreticalMean <- round(1/lambda), 3)
cbind(simulatedMean, theoreticalMean)
```

##  Sample Variance versus Theoretical Variance










)


#############
## showing how variable the sample variance is compared to the theoretical variance
#############
varSample <- round(var(subdata), 2)
varTheoretical <- round((1/lambdaa)^2, 2)
cbind(varSample, varTheoretical)

qplot(resampleSim, geom = "histogram", color = I('black'), fill = I('lightblue'))
                        




## second project


subdata2 <- ToothGrowth
dim(subdata2)
summary(subdata2)
any(is.na(subdata2))
head(subdata2)
tail(subdata2)
library(dplyr)
sub0.5 <- filter(subdata2, dose == .5)
t0.5 <- t.test(len~supp, data = sub)$conf.int
sub1 <- filter(subdata2, dose == 1.0)
t1.0 <- t.test(len~supp, data = sub2)$conf.int
sub2 <- filter(subdata2, dose == 2.0)
t2.0 <- t.test(len~supp, data = sub3)$conf.intrbind(t0.5, t1.0, t2.0)
