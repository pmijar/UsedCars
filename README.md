# What car features would impact price of a car?

![Image](images/kurt.jpeg)

## Overview

The goal for this project is to find out any available car feature that determines the price of a car. The objective is to provide clear insights to used car dealership with those features.


# Methodology used 

CRISP-DM (Cross Industry Standard  Process  for  Data  Mining)  methodology was used of to make it more repeatable and reliable.

![Image](images/crisp.png)


## Business Understanding

The Business understanding of the ask for the project was determined and based on it crafted the question about business need.

Question: Based on the used car features a car price is being determined, As a Used car inventory dealer,what car feature does fetch a good price

Solution needed: Determine the top 3 features from used car inventory, that would help used car dealer to keep those inventories fetching him/her a good car price.

## Data Understanding

Once the business case was identified, Loaded the used dataset into pandas Dataframe. Applied various querying methods on each of the features to understand the quality of data. 
- Missing Data ( Null Values) what percent was missing, if > 50% we plan to drop that feature
- Unique values within each categorical feature to look for inconsistencies
- Look for data distribution and any outliers 

## Data Preparation

After having an data understanding the following criterion were applied:

- Drop any features that does not value to the output depenedent variable 'Price'
- Impute the missing values based on numerical and categorical features
    - For numerical feature KNNImputer was applied
    - For categorical feature LabelEncoder was applied
- Apply the outlier filter on the features (This will reduce the sample observation)
    - Price <0 and >70K was applied
    - Year is between 1980 and 2022
    - Odometer < 500K

## Modeling

Following Models were applied, 'neg_mean_squared_error' scoring mechanism was used in GridSearchCV

1. Simple Linear Regression
2. Linear Regression with Polynomial Features using a GridSearchCV (with 5 fold cross validation)
3. Lasso Regression with Polynomial Features using a GridSearchCV (with 5 fold cross validation) to determine hyperparameter
4. Ridge Regression with Polynomial Features(degree=3) using a GridSearchCV (with 5 fold cross validation) to determine hyperparameter


Executing each model and capturing the mse/mae/r2 values across all four models identified 

## Evaluation

-   Based on the each of the four models that were evaluated, the MSE/MAE/R2 plot were presented.
-   For each of the four models that was evaluated the top feature importance was determined across all the models were:
    - Year
    - Odometer
    - Fuel
    - Drive
    - Cylinders


Ridge Regression with Polynomial Features(degree=3) was selected based on mse/mae/r2 values across the models


## Deployment

Based on the top feature importance year and odometer was able to analyze the data further to provide more insights within each of the features as below:

** Observation on Average Price impacts by year and odometer reading of used car:
- Average Price fetched by used car decreases until 350K odometer reading.
- Average Price fetched by used car has increasing trend after 350K odometer reading.
- After using year and odometer reading together, shows that older cars having higher odometer reading can fetch higher average price. we may be looking at Vintage cars.
