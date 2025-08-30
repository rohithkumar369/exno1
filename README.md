# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.
# Name:S.Rohith kumar
# Reg no:212224240153
# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df
```

# output:
<img width="1218" height="746" alt="Screenshot 2025-08-30 111839" src="https://github.com/user-attachments/assets/31831fbe-cf29-41b3-9e67-38a1a0f532fe" />

```
df.head()
```

# output:
<img width="1147" height="240" alt="image" src="https://github.com/user-attachments/assets/bb737449-7c39-4974-a2e9-a2ac7ea15c46" />

```
df.tail()
```

# output:
<img width="1177" height="310" alt="image" src="https://github.com/user-attachments/assets/e320805c-a3e0-4351-84d1-7ab575d07215" />

```
df.isnull()
```

# Output:
<img width="970" height="817" alt="Screenshot 2025-08-30 131120" src="https://github.com/user-attachments/assets/4d80941d-57e8-443f-8d7e-3c0415b17c37" />

```
df.isnull().sum()
```

# Output:
<img width="316" height="632" alt="Screenshot 2025-08-30 131241" src="https://github.com/user-attachments/assets/69a39b4b-cd98-40d2-ba13-0f7fefe3efa1" />

```
df.isnull().any()
```

# Output:
<img width="250" height="622" alt="image" src="https://github.com/user-attachments/assets/71aa06fd-a333-44c1-8f40-d01261a6e7b8" />

```
df.dropna(axis=0)
```

# Output:
<img width="1193" height="577" alt="image" src="https://github.com/user-attachments/assets/718ab934-0643-481e-8f0f-67998008578e" />

```
df.dropna(axis=1)
```

# Output:
<img width="400" height="812" alt="image" src="https://github.com/user-attachments/assets/44f13d41-b426-4aa1-8329-035488dc0066" />

```
df.fillna("empty")
```

# Output:
<img width="1276" height="802" alt="image" src="https://github.com/user-attachments/assets/fc4a62d1-75e5-44bd-a883-c403b8560a08" />

```
df.fillna(method='ffill')
```

# Output:
<img width="1098" height="816" alt="image" src="https://github.com/user-attachments/assets/ffcde532-c0f4-40b9-b2a4-cb483cad1b97" />

```
df.fillna(method='bfill')
```

# Output:
<img width="1072" height="778" alt="image" src="https://github.com/user-attachments/assets/d2fe5235-5052-4b45-8d34-a539681f1f98" />

```
df.fillna({'NAME':'HARI','GENDER':'MALE','ADDRESS':'CHITHOR','M1':90,'M2':90,'M3':89,'M4':87})
```

# Output:
<img width="1170" height="808" alt="image" src="https://github.com/user-attachments/assets/afa332fc-e696-4b01-a6f8-d8a3afd7ee22" />

```
ir=pd.read_csv("iris.csv")
ir
```

# Output:
<img width="773" height="516" alt="image" src="https://github.com/user-attachments/assets/f0d90241-c1ee-4a57-a327-0395949af5f1" />

```
ir.describe()
```

# Output:
<img width="753" height="363" alt="image" src="https://github.com/user-attachments/assets/cab3ebd8-355a-400b-9fa9-4ac1d491705b" />

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```

# Output:
<img width="713" height="570" alt="image" src="https://github.com/user-attachments/assets/adc0a707-8f20-436b-b899-e119f7c893ef" />

```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```

# Output:

<img width="118" height="45" alt="image" src="https://github.com/user-attachments/assets/e46ca3e0-ba80-409f-82c8-c5d7015576e9" />

```
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```

# Output:

<img width="265" height="258" alt="image" src="https://github.com/user-attachments/assets/eab8e5c5-7277-41d6-80d1-0e7c18c34d59" />

```
delid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
delid
```

# Output:

<img width="801" height="520" alt="image" src="https://github.com/user-attachments/assets/e866b58b-7fd1-4495-9d5d-e3cbdba749b9" />

```
sns.boxplot(x='sepal_width',data=delid)
```

# Output:

<img width="742" height="567" alt="image" src="https://github.com/user-attachments/assets/6bb04b37-3b5b-4714-8495-601001799b5f" />

```
import numpy as np
from scipy import stats
z = np.abs(stats.zscore(ir['sepal_width']))
z
```

# Output:


<img width="827" height="667" alt="image" src="https://github.com/user-attachments/assets/16d75cb3-f8d3-4cc3-8ce9-eb2c9811d035" />

```
ir1=ir[z<3]
ir1
```

# Output:

<img width="807" height="521" alt="image" src="https://github.com/user-attachments/assets/f70da3c0-f325-4ef0-8e90-994d14deb9a9" />

# Result

Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
