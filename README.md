# Explainable Air Quality Prediction Using Ensemble Learning and SHAP

An academic machine-learning project that estimates AQI from pollutant measurements, predicts next-day AQI, compares ensemble regression models, and explains model predictions with SHAP.

## Project workflow
1. Load daily pollutant records for 10 Indian cities.
2. Combine city-wise CSV files and inspect data quality.
3. Prepare pollutant features and derive pollutant sub-indices using the breakpoint logic implemented in the notebook.
4. Estimate overall AQI using the maximum pollutant sub-index.
5. Construct a next-record AQI target within each location.
6. Evaluate using a chronological train/test split.
7. Compare Random Forest, XGBoost, LightGBM, and CatBoost.
8. Interpret the selected model with SHAP.

## Dataset
Source: [Indian Cities AQI 2020–2024 (Kaggle)](https://www.kaggle.com/datasets/rajanbhateja/indian-cities-aqi-2020-2024)

The dataset used in the project contains 18,270 rows from 10 Indian cities, with seven pollutant variables: PM2.5, PM10, NO2, NH3, SO2, CO, and O3. Download the dataset separately and check its license before use. The raw dataset is intentionally not committed to this repository.

## Run in Google Colab
1. Open the notebook in `notebooks/` using Google Colab.
2. Download the Kaggle dataset archive.
3. Run the notebook and upload the ZIP archive when prompted.

## Dependencies
See [requirements.txt](requirements.txt).

## Methodological notes
- AQI values are breakpoint-derived estimates based on the available pollutant data. Do not describe them as official CPCB observations without verifying pollutant units, averaging periods, and the complete official procedure.
- The notebook's shifted target is the next available record per location; verify that records are consecutive calendar days before calling it next-calendar-day prediction.
- Fit imputers on training data only to avoid information leakage from the test period.
- SHAP describes model feature attributions; it does not establish causality.
- Re-run the notebook in a clean environment and record actual metrics and package versions before making final performance claims.

## Academic context
B.Tech CSE (AI & Data Science)  
MIT World Peace University, Pune

## Disclaimer
For academic and research purposes only. This is not a certified air-quality monitoring service and must not be used as the sole basis for medical, regulatory, or emergency decisions.
