# Summary report


Project: Smart Factory Energy Prediction Challenge

Author: Shivam Kumar

1. Problem Statement

SmartManufacture Inc. seeks to forecast equipment energy consumption in an industrial facility using environmental and sensor data. The goal is to enable energy optimization and cost reduction by developing a regression-based predictive model.

2. Data Overview

The dataset includes:

Timestamps of sensor readings

Equipment and lighting energy consumption

Temperature and humidity from 9 factory zones

Outdoor weather data (temperature, humidity, pressure, etc.)

Two synthetic features: random_variable1 and random_variable2

Total missing values were ∼5% across nearly all features.

3. Exploratory Data Analysis (EDA)

Key insights:

-->Energy consumption is moderately skewed

-->Usage varies significantly by hour and day of the week (higher during work hours)

-->Zone temperature and humidity are moderately correlated with energy use

-->Time-based features (hour, day_of_week) show predictive potential

4. Data Preprocessing

-->Converted timestamp to datetime and extracted hour, day_of_week, and month

-->Imputed missing values using median imputation for robustness

-->Converted all object-type numerical columns to float64

-->Handled outliers using IQR filtering (only for target variable)

5. Feature Engineering

Created new features:

-->avg_zone_temperature: Mean temperature across all 9 zones

-->avg_zone_humidity: Mean humidity across all 9 zones

-->temp_humidity_interaction: Interaction term between temperature and humidity

6. Feature Selection: Random Variables

-->Analyzed random_variable1 and random_variable2:

-->Very low correlation with the target

-->Low feature importance in Random Forest

-->RMSE slightly improved when these were excluded

Conclusion: These variables were excluded from the final model.

7. Model Development

Models Compared:

Linear Regression

Random Forest (Baseline + Tuned)

XGBoost

Final Model Chosen:

Random Forest with hyperparameter (Tuned)

Hyperparameters (Best):

n_estimators: 200

max_depth: None

min_samples_split: 5

min_samples_leaf: 2

8. Final Evaluation

Tuned Random Forest is clearly better than the baseline on all key metrics:

It reduces the prediction error (both MAE and RMSE).

It achieves a higher R², meaning it explains more variance in the target.

Even if the performance gain seems modest, this is often expected in real-world energy data, where sensor noise and environmental variability can cap prediction power.

-->Tuned RF showed consistent improvement across all metrics.

9. Key Recommendations

Focus on managing zone humidity and temperature (especially during peak hours)

Consider operational changes during high energy use time windows

Use this model to guide energy scheduling and real-time energy monitoring

10. Deliverables


Next Steps

Test final model on SmartManufacture Inc.'s private holdout set

Consider further tuning or ensembling if results remain weak

Integrate model with a dashboard for live monitoring and alerts