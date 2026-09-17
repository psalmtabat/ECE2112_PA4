# ECE2112_PA1
**Made by: Psalm I. Tabat | 2ECE-C**

This repository contains my submission for Programming Assignment No. 4 of "Advanced Computer Programming and Algorithms" for A.Y. 2026-2027. It covers three Python exercises from Module 4 - Data Wrangling and Visualization.

Before all codes were executed, Pandas and Matplotlib library was loaded and renamed as "pd" and "plt" respectively. Additionally, an xlsx dataset, board2.xlsx, was loaded into a Pandas DataFrame named `df`:
```python
import pandas as pd
import matplotlib.pyplot as plt
```

lastly, the average of the scores of all the subject of each student was taken:
```python
df['Average'] = df[['Math','Electronics','GEAS','Communication']].mean(axis=1)
```

# A. VISAYAS COMMUNICATION DATAFRAME

Create a DataFrame named VisComm containing students whose Hometown is Visayas and whose Track is Communication. Retain only these columns, in the stated order: `Name, Gender, Math, Electronics, Average`

Display the resulting DataFrame and its number of rows. Both filtering conditions must be applied to the source dataset before the columns are selected.

```python
VisComm = df.loc[(df['Hometown']=='Visayas')&(df['Track']=='Communication'),['Name','Gender','Math','Electronics','Average']]
```

# B. VISAYAS FEMALE DATAFRAME

Create a second DataFrame named VisFemale containing students whose Hometown is Visayas andwhose Gender is Female. Retain only: `Name, Track, GEAS, Electronics, Average`

```python
VisFemale = df.loc[(df['Hometown']=='Visayas')&(df['Gender']=='Female'),['Name','Track','GEAS','Electronics','Average']]
```

Display VisFemale. Then display only the rows of VisFemale whose Average is at least 60. Do not overwrite VisFemale when performing this second filter.

```python
VisFemale.loc[VisFemale['Average']>=60]
```

# C. CATEGORY-AVERAGE VISUALIZATION

Examine how the recorded Average differs across the three categorical features Track, Gender, and Hometown.

&emsp;a. For each feature, compute the mean of Average for every category using Pandas.
```python
ave_track = df.groupby('Track')['Average'].mean()
ave_gender = df.groupby('Gender')['Average'].mean()
ave_hometown = df.groupby('Hometown')['Average'].mean()
```
&emsp;b. Display the three summary tables.

&emsp;c. Create one figure containing three bar charts: mean Average by Track, by Gender, and by Hometown.
```python
fig, ax = plt.subplots(1,3, figsize = (15,5))
ax[0] = df.groupby('Track')['Average'].mean().plot(kind='bar', ax=ax[0])
ax[1] = df.groupby('Gender')['Average'].mean().plot(kind='bar', ax=ax[1])
ax[2] = df.groupby('Hometown')['Average'].mean().plot(kind='bar', ax=ax[2])
plt.show()
```
&emsp;d. Below the figure, write three concise statements identifying the category with the highest sample mean for each feature.
```python
print('The track with the highest average is', df.groupby('Track')['Average'].mean().idxmax(),'with', df.groupby('Track')['Average'].mean().max())
print('The gender with the highest average is', df.groupby('Gender')['Average'].mean().idxmax(),'with', df.groupby('Gender')['Average'].mean().max())
print('The hometown with the highest average is', df.groupby('Hometown')['Average'].mean().idxmax(),'with', df.groupby('Hometown')['Average'].mean().max())
```

#### **README file Version History:**
September 17, 2026 - Initial README output uploaded.
