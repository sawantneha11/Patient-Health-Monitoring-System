# Patient Health Monitoring System

## Description
This project monitors and analyzes patient health data in real-time. It collects data from wearable devices and medical records, preprocesses it, detects anomalies using machine learning, and provides visualizations and alerts for healthcare providers.

## Goals
1. Data Collection: Gather health data from wearables and records.
2. Data Preprocessing: Clean and preprocess the data.
3. EDA: Understand health trends and patterns.
4. Anomaly Detection: Implement ML algorithms.
5. Visualization: Display health trends and anomalies.
6. Alerts: Real-time alerts for anomalies.
7. Deployment: Create a web app using Flask/Django.

## Tech Stack
- **Languages:** Python
- **Libraries:** Pandas, NumPy, Scikit-Learn, TensorFlow/Keras, Flask/Django, Matplotlib, Plotly/Dash
- **Tools:** Jupyter Notebook, Git, Docker
- **Database:** PostgreSQL/MySQL
- **Cloud:** AWS/GCP/Azure (optional)

## Structure
```
patient-health-monitoring/
├── data/
├── notebooks/
│   ├── data_collection.ipynb
│   ├── data_preprocessing.ipynb
│   ├── exploratory_data_analysis.ipynb
│   ├── anomaly_detection.ipynb
├── src/
│   ├── data_collection.py
│   ├── data_preprocessing.py
│   ├── anomaly_detection.py
│   ├── app.py
├── requirements.txt
├── Dockerfile
├── README.md
└── .gitignore
```

## Setup
1. Clone the repo.
2. Install dependencies: `pip install -r requirements.txt`
3. Run notebooks for each step.
4. Deploy the app: `python src/app.py`

## Example Code Snippets
**Data Collection:**
```python
import pandas as pd

# Example data collection function
def collect_health_data(file_path):
    data = pd.read_csv(file_path)
    return data

# Example usage
file_path = 'data/health_data.csv'
data = collect_health_data(file_path)
print(data.head())
```

**Anomaly Detection with Isolation Forest:**
```python
import pandas as pd
from sklearn.ensemble import IsolationForest

# Load and preprocess data
data = pd.read_csv('data/health_data.csv')
features = data[['heart_rate', 'blood_pressure', 'temperature']]

# Train Isolation Forest model
model = IsolationForest(contamination=0.1)
model.fit(features)

# Predict anomalies
data['anomaly'] = model.predict(features)
data['anomaly'] = data['anomaly'].map({1: 0, -1: 1})  # Convert to binary (0: normal, 1: anomaly)

# Example usage
print(data[data['anomaly'] == 1])
```
