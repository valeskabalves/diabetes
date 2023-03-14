# PIMA Indians Diabetes
This dataset is originally from the National Institute of Diabetes and Digestive and Kidney Diseases.

The objective is to predict based on diagnostic measurements whether a patient has diabetes.

Several constraints were placed on the selection of these instances from a larger database. In particular, all patients here are females at least 21 years old of Pima Indian heritage.

- **Pregnancies:** Number of times pregnant
- **Glucose:** Plasma glucose concentration a 2 hours in an oral glucose tolerance test
- **BloodPressure:** Diastolic blood pressure (mm Hg)
- **SkinThickness:** Triceps skin fold thickness (mm)
- **Insulin:** 2-Hour serum insulin (mu U/ml)
- **BMI:** Body mass index (weight in kg/(height in m)^2)
- **DiabetesPedigreeFunction:** Diabetes pedigree function
- **Age:** Age (years)
- **Outcome:** Class variable (0 or 1) 1: Diabetic, 0: Healty

## Dataset shape
The dataset has 768 rows and 9 columns and all dataset features are numeric with no null values.

## Correlation
There is a strong positve correlation between Pregnancies and Age, Glucose and Outcome. 
There is a strong negative correlation between Skinthickness and Age, Pregnancies and SkinThickness, Pregnance and Insulin

Glucose is the most correlated feature and BloodPressure is the least correlated feature.

## Outliers
There are some outliers analyzed through the distribution of data in the histograms and boxplots and they were removed through the IQR.

## Standardize features
The features were standardize by removing the mean and scaling to unit variance.

## ML Model Assessment
- Precision: Out of all the patients that the model predicted would get diabetes, 78% actually did.
- Recall: Out of all the patients that actually did get diabetes, the model predicted this outcome correctly for 48% of those patients.
- F1 Score: 0.59 - Since this value is close to 1, it tells us that the model does a good job of predicting whether or not patients will get diabetes.
2 * (Precision * Recall) / (Precision + Recall) ***** 2 * (.78 * .48) / (.78 + .48)
- Support: These values is regarding how many patients belonged to each class in the test dataset. Among the patientis in the test dataset, 127 did not get diabetes and 65 did get diabetes.

## Confusion Matrix
TN: 118 patients without diabetes were correctly predicted as no diabetics
FP: 9 patients without diabetes were incorrectly predicted as diabetics
FN: 34 patients with diabetes were incorrectly predicted as no diabetics
TP: 31 patients with diabetes were correctly predicted as diabetics

## Result
The choice of metrics depends on the business objective.

For this project, sensibility (False Negative) is the metric most important, since predicting diabetics as no diabetics is the worst expected error. This may imply no further investigations and consequently no treatment of the disease.

So the better result is to have a Sensitivity (The correct prediction for positive values) result higher than a Specificity (The correct prediction for negative values) result.

The error in predicting a healthy patient as a diabetic patient is more acceptable than the opposite.

## Threshold Adjustment
With a threshold of 0.242365, the sensitivity has increased from 0.48 to 0.85, and the specificity has decreased from 0.93 to 0.75. Despite the decrease in specificity, for this project, the most important metric is sensitivity, once we want to correctly predict the patients with diabetes, the correct prediction for positive values.

The AUC has also increased after threshold adjustment, from 0.70 to 0.79.
