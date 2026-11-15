# SpectralCrop — Hyperspectral Crop Stress Detection & Temporal Forecasting

Day 1 Setup, Scope Confirmation, Environment Verification, and Dataset Decision Repository.

## Project Scope

1. **Detection Baseline:** Classify leaf/plant spectral reflectance observations into healthy vs. stressed/diseased states using tabular spectral features and vegetation indices (`scikit-learn`, `XGBoost`).
2. **Simple Temporal Forecast:** Forecast next-timestep vegetation index / stress trajectory ($\Delta\text{NDVI}_{t+1}$) across repeated measurement dates.
3. **Interactive Workbench:** Web console (`server.ts` + React `src/`) to audit repository structure, execute live Python stack verification, inspect spectral curves, and edit Day 1 documentation.

---

## Repository Structure

```text
.
├── app/                      # Web application architecture notes & integration docs
├── data/
│   ├── raw/                  # Downloaded Zenodo CC-BY-4.0 CSVs + clearly labeled synthetic fallback CSV
│   └── processed/            # Output directory for Day 2+ cleaned tables & split manifests
├── docs/
│   ├── project_brief.md      # One-page project brief: problem, data, success metrics
│   ├── dataset_note.md       # Dataset source, licence, shape, labels, and grouping columns
│   └── mentor_message.md     # Block 1 mentor scope confirmation & cadence message
├── notebooks/
│   └── 01_day1_env_and_data_check.ipynb  # Day 1 environment & spectral sanity-check notebook
├── reports/                  # Generated evaluation figures and metrics reports
├── src/
│   └── pipeline/
│       ├── verify_env.py                 # Core Python library import verification script
│       ├── dataset_loader.py             # CSV loader & spectral summary inspector
│       └── generate_synthetic_spectra.py # Fallback #3 synthetic controlled-stress spectra generator
├── README.md
└── requirements.txt
```

---

## Quickstart & Environment Verification (Block 3)

### 1. Python Stack Setup

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

### 2. Verify All Core Library Imports

```bash
python3 src/pipeline/verify_env.py
```

Required packages verified: `numpy`, `pandas`, `scikit-learn`, `xgboost`, `matplotlib`, `spectral`.

### 3. Inspect Dataset & Launch Interactive Workbench

```bash
python3 src/pipeline/dataset_loader.py
npm install
npm run dev
```

---

## Day 1 Carry-Forward to Day 2 & Day 5

- **Leak-Free Grouping Keys:** `Plant_ID`, `Pot_Number`, `date`, `TimeStamp` (and `plant_id`, `plot_id`, `field_id`, `acquisition_date` in the synthetic benchmark).
- **Rule:** All Day 5 cross-validation must group by `Plant_ID` (`StratifiedGroupKFold`) and respect chronological `date` ordering for temporal forecasts.

## Pushing to GitHub

```bash
git remote add origin <YOUR_GITHUB_REPO_URL>
git branch -M main
git push -u origin main
```
