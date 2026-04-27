# Air Quality Prediction using Machine Learning

This repository presents an end-to-end machine learning pipeline for predicting urban air quality, with a focus on carbon monoxide concentration (`CO(GT)`) using the Air Quality dataset.

---

## Project Overview

This project develops and compares multiple regression models to predict CO concentration from sensor and gas measurements. The work includes data preprocessing, feature scaling, model training, evaluation, cross-validation, and error analysis.

**Problem type:** Supervised regression  
**Models used:** Random Forest, SVR, XGBoost, Gradient Boosting Regressor  
**Best model:** XGBoost

---

## Dataset

- Dataset file: `AirQuality.csv`
- Total records used after cleaning: 7,674
- Number of input features: 16
- Target variable: `CO(GT)`
- Data frequency: Hourly observations
- Date range: 10 March 2004 to 4 April 2005

Example input features:

- `PT08.S2(NMHC)`
- `C6H6(GT)`
- `NOx(GT)`
- `PT08.S1(CO)`
- `NO2(GT)`

A combined `DateTime` field was created from the original date and time columns, and invalid or missing values were removed during preprocessing.

---

## Methodology

### Data Preprocessing

- Loaded the dataset into a pandas DataFrame
- Combined date and time into a single `DateTime` column
- Removed invalid and missing values
- Selected 16 numerical predictor variables
- Used `CO(GT)` as the target variable
- Split the data into training and testing sets
- Applied feature scaling using `StandardScaler`

### Train-Test Split

- Training samples: 6,139
- Testing samples: 1,535
- Split ratio: 80% training / 20% testing

### Models Implemented

- Random Forest Regressor
- Support Vector Regressor (SVR)
- XGBoost Regressor
- Gradient Boosting Regressor

### Evaluation Metrics

- RMSE
- MAE
- R² score
- 5-fold cross-validation

---

## Results

### Model Performance

| Model | RMSE | MAE | R² |
|---|---:|---:|---:|
| XGBoost | 0.2879 | 0.1894 | 0.9602 |
| SVR | 0.2947 | 0.1812 | 0.9583 |
| Gradient Boosting | 0.3182 | 0.2096 | 0.9514 |
| Random Forest | 0.3518 | 0.2208 | 0.9406 |

XGBoost achieved the best overall performance on the test set.

### Cross-Validation (Mean R²)

- Random Forest: 0.9303
- XGBoost: 0.9514
- Gradient Boosting: 0.9464

### Important Features

Top influential features identified through tree-based models:

1. `PT08.S2(NMHC)`
2. `C6H6(GT)`
3. `NOx(GT)`
4. `PT08.S1(CO)`
5. `NO2(GT)`

---

## Visualisations and Outputs

The notebook generates:

- Actual vs predicted plots for all models
- Error distribution plots
- Model comparison plots
- Cross-validation boxplots
- Feature importance plots

The repository also includes:

- `FP_AIR_QUALITY.ipynb` — main notebook
- `AirQuality.csv` — dataset
- `actual_vs_predicted_results.csv` — model predictions and errors

---

## Repository Structure

```text
.
├── FP_AIR_QUALITY.ipynb
├── AirQuality.csv
├── actual_vs_predicted_results.csv
├── README.md
└── requirements.txt
```

---

## Installation

```bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>

python -m venv .venv
source .venv/bin/activate   # On Windows: .venv\Scripts\activate

pip install -r requirements.txt
```

Example `requirements.txt`:

```text
pandas
numpy
scikit-learn
xgboost
matplotlib
seaborn
```

---

## Usage

1. Open `FP_AIR_QUALITY.ipynb` in Jupyter Notebook, VS Code, or Google Colab.
2. Run all cells from top to bottom.
3. The notebook will:
   - Load and preprocess the data
   - Split and scale the dataset
   - Train all models
   - Evaluate model performance
   - Generate visualisations
   - Export prediction results

---

## Key Findings

- XGBoost delivered the highest predictive performance.
- SVR also performed strongly with competitive error metrics.
- Tree-based models showed that gas sensor readings and nitrogen compounds are strong predictors of CO concentration.
- Cross-validation results indicate good generalisation.

---

## Future Work

- Add temporal features such as hour, day, and season
- Explore deep learning models such as LSTM
- Include external meteorological variables
- Deploy the best model as a web application or API

---

## Acknowledgement

This project uses the Air Quality dataset for regression-based air pollution prediction and analysis.
