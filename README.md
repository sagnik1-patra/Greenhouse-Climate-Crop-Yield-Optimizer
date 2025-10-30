🌿 BioSphere — Prediction Module

AI-Powered Greenhouse Climate & Crop Yield Forecasting System

This repository contains the prediction-only pipeline for the BioSphere project.
It loads a pre-trained hybrid-optimized LSTM model and generates yield and climate predictions using historical greenhouse data.
All results are saved as .csv and .json files for further visualization or integration into dashboards.

📁 Project Directory
C:\Users\NXTWAVE\Downloads\Greenhouse Climate & Crop Yield Optimizer\
│
├── archive/
│   └── 20210703_greenhouse_data.csv         # Input dataset
│
├── biosphere_model.h5                       # Trained hybrid LSTM model
├── biosphere_scaler.pkl                     # Saved MinMax scalers
├── biosphere_config.yaml                    # Configuration summary
│
├── biosphere_predict.py                     # Prediction script (this file)
├── biosphere_results.csv                    # Actual vs Predicted values
├── biosphere_prediction.json                # Summary of metrics + samples
└── (Optional Graphs)
    ├── biosphere_accuracy_graph.png
    ├── biosphere_comparison_graph.png
    ├── biosphere_prediction_graph.png
    └── biosphere_result_graph.png

⚙️ Requirements

Python Version: 3.10 or above

Install dependencies:

pip install tensorflow==2.15 pandas numpy scikit-learn matplotlib seaborn pyyaml

🧠 How It Works

Model Loading — Loads your saved .h5 LSTM model and MinMax scalers (.pkl).

Data Preprocessing — Reads and cleans the greenhouse dataset (semicolon separated).

Scaling — Normalizes feature and target data using the original training scalers.

Sequence Generation — Builds time-series windows for the LSTM.

Prediction & Evaluation — Generates predictions and computes:

MAE (Mean Absolute Error)

RMSE (Root Mean Squared Error)

R² (Coefficient of Determination)

Saving Results — Stores results in both .csv and .json formats.

🚀 Running the Prediction

Step 1: Make sure your model files (.h5, .pkl, .yaml) are in the same directory.

Step 2: Run the script:

python biosphere_predict.py


Step 3: Check the generated files:

biosphere_results.csv → full Actual vs Predicted table

biosphere_prediction.json → compact JSON summary with metrics

📊 Output Files
✅ biosphere_results.csv

Contains all actual and predicted yield/climate values.

Actual	Predicted
45.21	46.08
47.11	46.80
49.00	49.32

![Confusion Matrix Heatmap](aCSA_ACO_biosphere_result_graph.png)

✅ biosphere_prediction.json
{
  "dataset": "C:\\Users\\NXTWAVE\\Downloads\\Greenhouse Climate & Crop Yield Optimizer\\archive\\20210703_greenhouse_data.csv",
  "records_evaluated": 17562,
  "metrics": {
    "MAE": 0.892,
    "RMSE": 1.305,
    "R2": 0.941
  },
  "sample_predictions": [
    {"actual": 45.22, "predicted": 46.05},
    {"actual": 47.13, "predicted": 46.78}
  ]
}

🧾 Configuration Reference (biosphere_config.yaml)

Stores metadata and model parameters:

optimizer: Hybrid CSA + ACO
dataset: C:\Users\NXTWAVE\Downloads\Greenhouse Climate & Crop Yield Optimizer\archive\20210703_greenhouse_data.csv
features:
  - greenhouse_temperature
  - greenhouse_humidity
target: crop_yield
time_steps: 5
metrics:
  MAE: 0.892
  RMSE: 1.305
  R2: 0.941

💡 Key Features

Supports hybrid optimizers (PSO, AIS, CSA, ACO)

Fully automated preprocessing for semicolon-separated greenhouse datasets

Outputs ready for Streamlit, Power BI, or FastAPI dashboards

Scalable to IoT sensor data streams (MQTT / Edge Devices)

🔋 Next Steps

You can extend this prediction system with:

Streamlit Dashboard — visualize graphs & metrics interactively.

FastAPI Service — host predictions for IoT devices.

Actuator Control Logic — trigger irrigation or ventilation changes automatically.

🧑‍💻 Author

Developed by: Sagnik Patra
Project: BioSphere — AI-Powered Greenhouse Climate & Crop Yield Optimizer
