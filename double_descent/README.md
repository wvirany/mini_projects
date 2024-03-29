## overparametrized polynomials

The purpose of this notebook was to investigate the idea that interpolating classifiers perform well when averaged together. Evidently, this was not the case. However, the literature indicates that certain overparametrized methods, e.g., AdaBoost and Random Forests (see Wyner et al. 2017), which interpolate the data are robust to noise. What is the difference?


## random forests as interpolating classifiers

The purpose of this notebook was to investigate the nature of random forests as interpolating classifiers in three different settings:

* An example with pure noise
* An example with signal and some noise
* An example with pure signal

The goal was to reproduce the "double descent" curve and examine what these classifiers look like in the underparameterized and overparameterized regimes, as well as at the interpolation threshold. Although I was unable to reproduce a "nice" double descent curve, I did gain some insight into why classifiers which interpolate noise can still generalize well, relating this to the "local spiked smoothing" phenomenon.

## reproducing double descent on MNIST dataset

Here I am able to reproduce the double descent curve; however, a question still remains: is this the true double descent phenomenon?

I think that we are restraining the model complexity until the point when we begin increasing the number of estimators, but is this really an example of double descent?

This experiment was performed to reproduce the results from Belkin et. al (2019), "Reconciling modern machine learning practice and the bias-variance tradeoff"

## k-Nearest Neighbors bias-variance tradeoff

The purpose of this notebook is to show an example in which double descent does not occur, i.e. one which exemplifies the classical bias-variance tradeoff. This experiment successfully showed the classical "U-shaped" curve as a function of the model complexity. It is known that RFs are a weighted version of kNN. From here, it would be interesting to investigate the theoretical reasons why RFs are robust to overfitting while kNN is not.

## AdaBoost as an interpolating classifier

This notebook demonstrates the ability of AdaBoost to fit to an arbitrary dataset, and furthermore, the ability to generalize well in the overparameterized regime. However, there is an issue here. Scikit-Learn implements an "early-stopping" mechanism which effectively regularizes the complexity of the AdaBoost classifier. Hence, I am unable to examine the loss surface as the complexity increases beyond the interpolation threshold. This will be addressed in the future.
