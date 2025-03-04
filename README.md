# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
# Data Cleaning
```py
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
![image](https://github.com/user-attachments/assets/30a7d399-2fcc-4722-959a-4d21ccd0e272)
```py
df.head()
```
![image](https://github.com/user-attachments/assets/0be6426f-a466-4730-b7a4-39bb5aed2321)

```py
df.tail()
```
![image](https://github.com/user-attachments/assets/5cef8819-dd4b-417d-ad2b-4958f894e4b3)

```py
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/8e9c9dac-51e7-4ddb-8503-2a32e4c43dad)
```py
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/5f9073e2-61a8-4d6d-8ba2-29a88e6f39ca)
```py
df.dropna()
```
![image](https://github.com/user-attachments/assets/3ca3202b-6d32-4d68-9d13-937aaba50a7b)

```py
df.fillna(1)
```
![image](https://github.com/user-attachments/assets/a92d820a-0e8b-48c4-ba7b-119803169157)

```py
df.fillna(method="ffill")
```
![image](https://github.com/user-attachments/assets/f28bd29f-4782-4756-8b9f-e483e99f9d56)

```py
df.fillna(method="bfill")
```
![image](https://github.com/user-attachments/assets/bc4bd6c3-2378-47f2-a1ce-07891de4899d)

```py
df.fillna({'NAME':'SAM','GENDER':'MALE','ADDRESS':'TAMBARAM','M1':80.0,'M2':85.,'M3':87.0,'M4':88.0,'TOTAL':340.0,'AVG':85.00})
```
![image](https://github.com/user-attachments/assets/c6875c74-d196-437a-a1b5-553b3954cc8a)

# IQR(Inter Quartile Range)

```py
ir=pd.read_csv("/content/iris.csv")
ir
```
![image](https://github.com/user-attachments/assets/047b46a6-23d9-426e-8d1a-6669858a0b57)

```py
ir.describe()
```
![image](https://github.com/user-attachments/assets/326c2f49-a91d-4c9b-8b67-de5efcbfde59)

```py
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/e023ab75-5f92-45d2-82ad-c1e48f998537)

```py
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```
![image](https://github.com/user-attachments/assets/5d1c1ffa-15a2-4dd2-82fe-c06aecab2602)

```py
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/7a13a5dc-ea28-41f8-9b33-6591aa0822e4)

```py
delid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
delid
```
![image](https://github.com/user-attachments/assets/2816f7c0-134a-4e14-bd64-97a5327463ac)

```py
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/33a48de0-73d4-4097-8ce1-40f0442a107b)

```py
import matplotlib.pyplot as plt
import scipy.stats as stats

zdata=pd.read_csv("/content/heights.csv")
zdata
```
![image](https://github.com/user-attachments/assets/c0be6cac-696e-4caf-9eb4-f65cc4369a01)

```py
z = np.abs(stats.zscore(zdata['height']))
z
```
![image](https://github.com/user-attachments/assets/195da89e-b358-446b-b846-6407ab533893)

# Result
Thus the data is cleaned and Outlayer is detected and removed using IQR and Z-score method.
