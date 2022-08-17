# Tensorflow Car Price Analysis
In this project, after extracting the data sets as csv, we tried to represent the car prices graphically and schematically by using data analysis and data visualization methods. We checked the connection of the car prices we analyzed with other data, then we created a 4-layer and 12-neuron system.


## Libraries and Utilities

```Python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sbn
```
### Let's take a look at our top five data

```Python
dataFrame=pd.read_excel("merc.xlsx")
dataFrame.head()
```

![image](https://user-images.githubusercontent.com/67556543/185145085-22dc17e6-876c-4aaa-bca0-2bcec7d760ac.png)


```Python
dataFrame.describe()
```
![image](https://user-images.githubusercontent.com/67556543/185145403-19647330-380b-4a34-8fc2-eea40d50e3b2.png)

### Car Price Analysis Graph

```Python
plt.figure(figsize=(7,5))
sbn.displot(dataFrame["price"])
```

![image](https://user-images.githubusercontent.com/67556543/185145650-e3f4f6de-2032-400d-a8f9-378d8a5f6a95.png)


### Car Price Analysis Grap

```Python
sbn.countplot(dataFrame["year"])
```
![image](https://user-images.githubusercontent.com/67556543/185145841-1cbf60df-8a30-4af8-a184-74a2804f8ec7.png)



### Price vs Miles

```Python
sbn.scatterplot(x="mileage",y="price",data=dataFrame)
```
![image](https://user-images.githubusercontent.com/67556543/185146361-27c54bd6-0d0a-4fad-adc8-fc512aa59d50.png)

### Price vs Year

```Python
sbn.scatterplot(x="year",y="price",data=dataFrame)
```
![image](https://user-images.githubusercontent.com/67556543/185146809-cd7260ed-c073-4c8f-8c07-252823a72dd9.png)

### Data Cleaning
```Python
Veritemizleme=dataFrame.sort_values("price",ascending=False).iloc[131:]
```
![image](https://user-images.githubusercontent.com/67556543/185147156-a0d3cacb-6117-4829-9ba7-f35424708868.png)

### Data Training
```Python
from sklearn.preprocessing import MinMaxScaler
scaler=MinMaxScaler()
x_train=scaler.fit_transform(x_train)
x_test=scaler.transform(x_test)

from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense

model=Sequential()
model.add(Dense(12,activation="relu"))
model.add(Dense(12,activation="relu"))
model.add(Dense(12,activation="relu"))
model.add(Dense(12,activation="relu"))
model.add(Dense(1))
model.compile(optimizer="adam",loss="mse")

model.fit(x=x_train,y=y_train,validation_data=(x_test,y_test),batch_size=250,epochs=300)

```

### Regression graph
```Python

plt.scatter(x=y_test,y=tahminDizisi)
plt.plot(y_test,y_test,"g-*")

```
![image](https://user-images.githubusercontent.com/67556543/185147861-08b18f58-6a70-4683-94d6-319bb50f0d5e.png)

