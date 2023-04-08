# Ex-04-Multivariate-Analysis

## Aim
To perform Multivariate EDA on the given data set.

##Explanation
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

## Algorithm

### Step1
Import the built libraries required to perform EDA and outlier removal.

### Step2
Read the given csv file.

### Step3
Convert the file into a dataframe and get information of the data.

### Step4
Return the objects containing counts of unique values using (value_counts()).

### Step5
Plot the counts in the form of Histogram or Bar Graph.

### Step6
Use seaborn the bar graph comparison of data can be viewed.

### Step7
Find the pairwise correlation of all columns in the dataframe.corr()

### Step8
Save the final data set into the file.

import pandas as pd 
import numpy as np 
import matplotlib.pyplot as plt
import seaborn as sns
df=pd.read_csv("/content/SuperStore (1).csv")
df.head()
![image](https://user-images.githubusercontent.com/86044259/192983247-080a1cdf-d71f-4913-8890-89369e5d6e8b.png)
df.info()
![image](https://user-images.githubusercontent.com/86044259/192983320-21d268f3-6d28-4460-b0a6-00e57f6f2bd2.png)
df.isnull().sum()
![image](https://user-images.githubusercontent.com/86044259/192983441-f91fd724-e3cb-46c6-ac15-50d53f2c09e7.png)
df['Postal Code']=df['Postal Code'].fillna(df['Postal Code'].mode()[0])
df.isnull().sum()
![image](https://user-images.githubusercontent.com/86044259/192983537-9b8dd5f1-eb23-4bc4-965f-e8f2e25ab404.png)
sns.scatterplot(df['Postal Code'],df['Sales'])
![image](https://user-images.githubusercontent.com/86044259/192983615-e492920f-973a-46df-9ab4-1c7f1b1b9265.png)
state=df.loc[:,["State","Sales"]]
state=state.groupby(by=["State"]).sum().sort_values(by="Sales")
plt.figure(figsize=(17,7))
sns.barplot(x=state.index,y="Sales",data=state)
plt.xticks(rotation = 90)
plt.xlabel=("STATES")
plt.ylabel=("SALES")
plt.show()
![image](https://user-images.githubusercontent.com/86044259/192983687-52f2360b-b6a4-4427-ac35-87bf6a0f226f.png)
state=df.loc[:,["State","Postal Code"]]
state=state.groupby(by=["State"]).sum().sort_values(by="Postal Code")
plt.figure(figsize=(17,7))
sns.barplot(x=state.index,y="Postal Code",data=state)
plt.xticks(rotation = 90)
plt.xlabel=("STATES")
plt.ylabel=("POSTAL CODE")
plt.show()
![image](https://user-images.githubusercontent.com/86044259/192983805-498d01ed-82fb-4640-a9e6-cb04ffd1b7e4.png)

state=df.loc[:,["Segment","Sales"]]
state=state.groupby(by=["Segment"]).sum().sort_values(by="Sales")
plt.figure(figsize=(17,7))
sns.barplot(x=state.index,y="Sales",data=state)
plt.xticks(rotation = 90)
plt.xlabel=("SEGMENT")
plt.ylabel=("SALES")
plt.show()
![image](https://user-images.githubusercontent.com/86044259/192983890-e9a1f972-7bb2-4717-83d5-d2bcabb36cd6.png)

sns.barplot(df['Postal Code'], df['Ship Mode'], hue=df['Region'])
![image](https://user-images.githubusercontent.com/86044259/192984032-51344a9a-cd50-4915-b85c-caff7f56c98d.png)
df.corr()
sns.heatmap(df.corr(),annot=True)
![image](https://user-images.githubusercontent.com/86044259/192984196-8316eda7-b9bc-4418-81b3-50cf3f78cd93.png)

## Result
Thus the program to perform EDA on the given data set is successfully executed.
