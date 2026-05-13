# : Car Price Prediction Model

## Main Notebook

[Open Notebook](./car-price-prediction-model_fin.ipynb)
## Project Overview

This project builds a regression model to predict **MSRP (manufacturer-suggested retail price)** for automobiles using car attributes such as engine power, cylinders, mileage, drivetrain, vehicle size, and year.

The goal is to identify which vehicle features are most strongly associated with price and to build a model that can estimate MSRP as accurately as possible.

---

## Problem Definition

This is a **supervised machine learning regression problem** because the target variable, **MSRP**, is continuous numeric data.

The notebook explores the full regression workflow:
- data inspection and cleaning
- handling missing values and duplicates
- categorical variable encoding
- exploratory data analysis
- simple regression models
- forward and backward variable selection
- final regression model evaluation

---

## Why This Problem Matters

Several stakeholders could benefit from a model like this:

- **Car manufacturers** can understand which vehicle features influence pricing.
- **Dealerships** can use the model to price inventory more accurately.
- **Consumers** can gain better price transparency.
- **Analytics teams** can support pricing strategy, forecasting, and market positioning.

This makes the problem useful from both a business and a consumer perspective.

---

## Dataset Description

The dataset contains more than 11,000 car records, where each row represents a vehicle and its features.

### Target Variable
- `MSRP`

### Main Predictors Used
- `Year`
- `Engine_HP`
- `Engine_Cylinders`
- `Number_of_Doors`
- `highway_MPG`
- `city_mpg`
- `Popularity`
- `Vehicle_Size`
- `Driven_Wheels`

The original dataset also includes other categorical attributes such as:
- `Make`
- `Model`
- `Engine_Fuel_Type`
- `Transmission_Type`
- `Market_Category`
- `Vehicle_Style`

Some of these were dropped after cleaning and preprocessing.

---

## Data Cleaning and Preprocessing

Several preprocessing steps were performed before modeling:

### 1. Standardized Column Names
Column names were cleaned by replacing spaces and special characters with underscores.

### 2. Removed Duplicate Rows
Duplicate records were identified and removed to avoid biasing the model.

### 3. Handled Missing Values
Missing numeric values were filled using the **median**.

### 4. Encoded Categorical Variables
The required categorical variables were transformed into numeric form:
- `Driven_Wheels` was converted using **OneHotEncoder**
- `Vehicle_Size` was converted using **OrdinalEncoder**

### 5. Dropped Unused Categorical Variables
The remaining categorical features not needed for modeling were removed.

After preprocessing, the dataset was ready for regression analysis.

---

## Exploratory Data Analysis

The notebook includes:
- summary statistics
- missing value checks
- duplicate checks
- histograms
- correlation matrix
- scatterplots for key predictors

### Key EDA Findings
- `Engine_HP` had the strongest positive correlation with `MSRP`
- `Engine_Cylinders` also had a strong positive relationship with price
- `Year` showed a positive relationship with MSRP
- `city_mpg` and `highway_MPG` had weak negative relationships with MSRP
- front-wheel drive vehicles appeared to be less expensive on average

Overall, the EDA showed that engine performance and vehicle type are important predictors of car price.

---

## Modeling Approach

### Simple Regression Models
Three simple regression models were trained and compared:
1. `MSRP ~ Engine_HP`
2. `MSRP ~ Engine_Cylinders`
3. `MSRP ~ log(Engine_HP)`

### Multiple Regression
To improve prediction quality, the notebook also performed:
- **Forward selection**
- **Backward elimination**

These methods were used to identify the most important predictors for a stronger final regression model.

---

## Feature Selection Results

### Forward Selection Selected Features
- `Engine_HP`
- `Vehicle_Size_Ordinal`
- `Engine_Cylinders`
- `highway_MPG`
- `Driven_Wheels_four wheel drive`
- `Driven_Wheels_rear wheel drive`
- `Popularity`
- `city_mpg`
- `Number_of_Doors`
- `Year`

### Backward Elimination Selected Features
- `Year`
- `Engine_HP`
- `Engine_Cylinders`
- `Number_of_Doors`
- `city_mpg`
- `Popularity`
- `Vehicle_Size_Ordinal`
- `Driven_Wheels_four wheel drive`
- `Driven_Wheels_rear wheel drive`

The two methods produced very similar results, which increases confidence that these predictors are meaningful.

---

## Final Model

The final model was chosen based on test-set performance.

### Final Selected Feature Set
- `Engine_HP`
- `Vehicle_Size_Ordinal`
- `Engine_Cylinders`
- `highway_MPG`
- `Driven_Wheels_four wheel drive`
- `Driven_Wheels_rear wheel drive`
- `Popularity`
- `city_mpg`
- `Number_of_Doors`
- `Year`

### Final Evaluation Metrics
- **MAE:** 19,948.80
- **MSE:** 2,671,063,187.78
- **R²:** 0.4487

### OLS Training Summary
- **Training R²:** 0.516

---

## Interpretation of Results

The final model shows that:
- **Engine_HP** and **Engine_Cylinders** are the strongest positive predictors of MSRP
- newer cars tend to be more expensive
- drivetrain and vehicle size also contribute to pricing
- the model captures the general pricing trend but struggles with very high-end vehicles

### Limitations
- large prediction errors still remain
- high-priced cars are harder to predict accurately
- multicollinearity may affect coefficient stability
- MSRP is highly skewed with extreme outliers

---

## Conclusions

This project shows that car prices can be partially explained using measurable vehicle features. A multiple regression model performs better than simple one-variable models, but there is still room for improvement.

The project is a strong example of:
- regression analysis
- feature selection
- data preprocessing
- model interpretation
- business-oriented machine learning

---

## Next Steps

Possible improvements include:
- log-transforming MSRP
- handling outliers more carefully
- reducing multicollinearity
- testing Ridge/Lasso regression
- comparing with tree-based models such as Random Forest or Gradient Boosting
- using cross-validation

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Statsmodels
- Jupyter Notebook

---

## Main Notebook

[Open Notebook](./Homework_2_Car_Price_Prediction.ipynb)

---

## Author

Your Name
