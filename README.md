# Time Series Forecasting using LSTM

## Overview

This project uses RNNs, specifically LSTM(Long Short-Term Memory) to predict future air pollution values based on historical time-dependent data. The main goal was to reduce the Root Mean Square Error(RMSE) through experimentation and model optimization.

## Data

The input data was sourced from [Kaggle](https://www.kaggle.com/competitions/assignment-1-time-series-forecasting-may-2025/overview)

## Report

[Link to the report](https://docs.google.com/document/d/1xBjvPp5Lr3GHHeH3zInZ2sGKCVMuYnspy6N-NNvEsOo/edit?usp=sharing)

## Model Architecture

The best performing model was made of 3 stacked layers, using Adam optimizer and it had a root mean squared error(RMSE) of 4483.3

## Results

| Experiment | Layers                   | Activation | Optimizer | Learning Rate | Batch Size         | Epochs | RMSE (Train, Test)  |
|------------|--------------------------|------------|-----------|----------------|---------------------|--------|---------------------|
| 1          | 32                       | relu          | Adam        | -              | 32                   | 10      | 5401.6                  |
| 2          | 64                       | tanh       | Adam      | 0.001          | 64                  | 20     | 5567.4        |
| 3          | 64, 32                   | tanh       | Adam      | 0.001          | 64                  | 20     | 5980.4        |
| 4          | 64, 32 + dropout=0.2     | tanh       | Adam      | 0.001          | 64                  | 50     | 5284.1        |
| 5          | 128, 64, 32, 16          | relu       | Adamax    | 0.001          | 32 + early stop=10  | 10     | 5201.9        |
| 6          | 256, 128, 64, 32, 16     | relu       | Adamax    | 0.001          | 64 + early stop=20  | 10     | 5098.9        |
| 7          | 32, 16, 8                | relu       | Adam      | 0.005          | 64                  | 50     | 4922.6        |
| 8          | 32, 16, 8                | relu       | Adam      | 0.005          | 32                  | 50     | 4702.6        |
| 9          | 32, 16, 8                        | relu         | Adam         | Adam              | 32                  | 20     | 4505.2        |
| 10         | 32, 16, 8                        | relu          | Adam      | 0.005          | 32                  | 50     | 4483.3        |
| 11         | 256, 128, 64, 32, 16     | relu       | RMSprop   | 0.001          | 32 + early stop=20  | 10     | 5139.6        |
| 12         | 128, 64, 32, 16          | relu       | RMSprop   | 0.001          | 32 + early stop=20  | 50     | 5030.2        |
 13         | 128, 64, 32              | relu       | Adamax    | 0.001          | 64                  | 20     | 5234.7              |
| 14         | 64, 64, 32               | tanh       | Adam      | 0.001          | 32                  | 20     | 5179.3              |


