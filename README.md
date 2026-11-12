# TSAF-Ex-3-Log-Transformation-of-International-Airline-Passenger-Data

## AIM:
To apply a logarithmic transformation to the International Airline Passenger time series and
compare the original and transformed data.

## PROGRAM:

```
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

# ----------------------------------
# 1. Load AirPassengers dataset
# ----------------------------------

df = pd.read_csv("AirPassengers.csv")
# Convert Month to datetime
df['Month'] = pd.to_datetime(df['Month'])
# Set Month as index
df.set_index('Month', inplace=True)
print("Original Data:")
print(df.head())

# ----------------------------------
# 2. Plot original time series
# ----------------------------------

plt.figure(figsize=(12, 5))
plt.plot(
 df.index,
 df['Passengers'],
 marker='o'
)
plt.title('International Airline Passengers')
plt.xlabel('Year')
plt.ylabel('Passengers (Thousands)')
plt.grid(True)
plt.show()

# ----------------------------------
# 3. Apply log transformation
# ----------------------------------

df['Log_Passengers'] = np.log(df['Passengers'])
print("\nLog Transformed Data:")
print(df.head())

# ----------------------------------
# 4. Plot log-transformed series
# ----------------------------------

plt.figure(figsize=(12, 5))
plt.plot(
 df.index,
 df['Log_Passengers'],
 marker='o'
)
plt.title('Log-Transformed Airline Passenger Data')
plt.xlabel('Year')
plt.ylabel('Log(Passengers)')
plt.grid(True)
plt.show()

# ----------------------------------
# 5. Compare the series
# ----------------------------------

fig, axes = plt.subplots(2, 1, figsize=(12, 8))
axes[0].plot(df.index, df['Passengers'])
axes[0].set_title('Original Airline Passenger Series')
axes[0].set_ylabel('Passengers')
axes[0].grid(True)
axes[1].plot(df.index, df['Log_Passengers'])
axes[1].set_title('Log-Transformed Airline Passenger Series')
axes[1].set_ylabel('Log(Passengers)')
axes[1].set_xlabel('Year')
axes[1].grid(True)
plt.tight_layout()
plt.show()

```

## OUTPUT:

<img width="783" height="485" alt="image" src="https://github.com/user-attachments/assets/4ffd0855-21a6-40ff-a8e2-c682f4bbf8a1" />

<img width="726" height="791" alt="image" src="https://github.com/user-attachments/assets/3c4eb0c1-ce24-4143-90e0-8bd95df45983" />
