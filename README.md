# Taipei Home Value Estimator

A small-sample regression benchmark for estimating house price per unit area from transaction and location features in the UCI Real Estate Valuation dataset.

## Dataset

Loads UCI dataset 477 through ucimlrepo. The row identifier is excluded from features. See the [UCI Real Estate Valuation dataset card](https://archive.ics.uci.edu/dataset/477/real+estate+valuation+data+set). The dataset contains only 414 observations, so holdout estimates are uncertain. No dataset copy is committed here.

## Run

```bash
python -m venv .venv
# Windows: .venv\Scripts\activate
# macOS/Linux: source .venv/bin/activate
pip install -r requirements.txt
python main.py
```

The first run needs network access to fetch the dataset. You can select a different output directory with `python main.py --output-dir results`.

## Method and outputs

- Fixed random 75/25 holdout with seed 42.
- Median imputation and a 400-tree random forest regressor.
- Reports MAE, RMSE, and R-squared alongside a median-target baseline.
- Writes `artifacts/metrics.json`, `artifacts/holdout_predictions.csv`, and `artifacts/model.joblib`.

This is an educational benchmark, not a property appraisal tool. The small, location-specific sample and random split do not establish accuracy for current market prices or other regions. No performance result is claimed until the script has been run and independently checked.
