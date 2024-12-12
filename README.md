# Driver-Fatigue-Project

## Introduction
Singapore, a densely populated city of over six million people, faces an increasing challenge with road safety due to the growing number of vehicles on its roads. The Singapore Police Force reports a worrying rise in accident fatalities, from `104` in 2022 to `131` in 2023 ([source](https://www.police.gov.sg/-/media/D4435F72157942D3B323EE4A507D4CFB.ashx)). Though driver fatigue is not the leading cause of road accidents, it is a significant contributing factor, especially when combined with other risky behaviors, such as driving under the influence of alcohol.

Research highlights the prevalence of sleepiness and fatigue among drivers in Singapore; one study found that `32.9%` of taxi drivers experience sleepiness and fatigue on the job ([source](https://pmc.ncbi.nlm.nih.gov/articles/PMC4350472/)). This underscores the need for measures to help drivers become more aware of their fatigue levels to reduce accident risks.

## Problem Statement
Drivers are often unaware of their fatigue levels, continuing to drive in a compromised state, which increases the risk of accidents. This project aims to develop a driver fatigue detection system that alerts drivers to their fatigue levels in real-time, providing an opportunity to prevent fatigue-related incidents and enhance road safety.

Reference : https://www.channelnewsasia.com/singapore/big-read-rising-traffic-accidents-road-culture-4328841

## Datasets
Majority of our datasets used will be from Kaggle. The possible datasets are as follows:
- https://www.kaggle.com/datasets/imadeddinedjerarda/mrl-eye-dataset

## Pre-requisites
- Must have a webcam for capturing the driver's facial features for fatigue detection.

## Steps to Run

1. **Install a Virtual Environment**:
   - To create and activate a virtual environment, run the following commands in your terminal:
     ```bash
     python -m venv venv
     source venv/bin/activate  # On Windows, use .\venv\Scripts\activate
     ```

2. **Install Dependencies**:
   - Install the required Python packages using `pip`:
     ```bash
     pip install -r requirements.txt
     ```

3. **Run the Project**:
   - Once the dependencies are installed, you can start the project by running the detection script:
     ```bash
     python detection.py
     ```

## Troubleshooting

- **Error: 'grab to failed frame'**
  - This error means that the webcam is not available or unable to open. Ensure that:
    - Your webcam is properly connected.
    - No other application is using the webcam.
    - You have the necessary permissions to access the webcam.
    
- **Error: 'ERROR: Could not install packages due to an OSError: [WinError 5]'**
  - This error typically occurs on Windows when you don't have sufficient permissions to install packages. To fix this:
    - Try running your IDE (e.g., VSCode) as **Administrator**.
    - Right-click on your IDE and select **Run as Administrator**.

- **Error: Depth Convolution Error while running `detection.py`**
  - If you encounter this error, change the model file in `detection.py`. On line 23, replace:
    ```python
    model = load_model('./content/model-after-augmv2.h5')
    ```
    with:
    ```python
    model = load_model('./content/model-after-augm.h5')
    ```
    This ensures the correct model is loaded for the detection.


## Directory Structure
```
Driver-Fatigue-System
├── content
│   ├── model-after-augm.h5
│   ├── model-after-augmv2.h5
│   ├── model.h5
│   └── model2.h5
├── Datasets
    ├── mrlEyes.py
├── dlib files
│   └── shape_predictor_68_face_landmarks.dat
├── evaluation
│   ├── head_tilt_eval.py
│   └── yawn_eval.py
├── haar cascade files
│   ├── haarcascade_eye_tree_eyeglasses.xml
│   ├── haarcascade_frontalface_alt.xml
│   ├── haarcascade_frontalface_alt2.xml
│   ├── haarcascade_lefteye_2splits.xml
│   ├── haarcascade_mcs_nose.xml
│   ├── haarcascade_profileface.xml
│   └── haarcascade_righteye_2splits.xml
├── model
│   └── transfer_learning.ipynb
├── detection.py
├──yawn.py 
├── head_tilt.py
├── README.md
├── alarm.wav
└──requirements.txt
```