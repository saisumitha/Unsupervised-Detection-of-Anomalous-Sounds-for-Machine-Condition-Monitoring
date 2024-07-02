# Our Speech Processing Project
This is a baseline system for **"Unsupervised Detection of Anomalous Sounds for Machine Condition Monitoring"**. 


## Description
The baseline system consists of two main scripts:
- `00_train.py`
  - This script trains models for each Machine Type by using the directory **dev_data/<Machine_Type>/train/** or **eval_data/<Machine_Type>/train/**.
- `01_test.py`
  - This script makes csv files for each Machine ID including the anomaly scores for each wav file in the directory **dev_data/<Machine_Type>/test/** or **eval_data/<Machine_Type>/test/**.
  - The csv files will be stored in the directory **result/**.
  - If the mode is "development", it also makes the csv files including the AUC and pAUC for each Machine ID. 



You can change the parameters for feature extraction and model definition by editing `baseline.yaml`.

### Run training script (for development dataset)
Run the training script `00_train.py`. 
Use the option `-d` for the development dataset **dev_data/<Machine_Type>/train/**.
```
$ python 00_train.py -d
```
`00_train.py` trains the models for each Machine Type and saves the trained models in the directory **model/**.

### Run test script (for development dataset)
Run the test script `01_test.py`.
Use the option `-d` for the development dataset **dev_data/<Machine_Type>/test/**.
```
$ python 01_test.py -d
```
The options for `01_test.py` are the same as those for `00_train.py`.
`01_test.py` calculates the anomaly scores for each wav file in the directory **dev_data/<Machine_Type>/test/**.
The csv files for each Machine ID including the anomaly scores will be stored in the directory **result/**.
If the mode is "development", the script also makes the csv files including the AUCs and pAUCs for each Machine ID. 

### 7. Check results
You can check the anomaly scores in the csv files in the directory **result/**.
Each anomaly score corresponds to a wav file in the directory **dev_data/<Machine_Type>/test/**:

`anomaly_score_fan_id_01.csv`
```  
normal_id_01_00000000.wav	6.95342025
normal_id_01_00000001.wav	6.363580014
normal_id_01_00000002.wav	7.048401741
normal_id_01_00000003.wav	6.151557502
normal_id_01_00000004.wav	6.450118248
normal_id_01_00000005.wav	6.368985477
  ...
```

Also, you can check the AUC and pAUC scores for each Machine ID:

`result.csv`
```  

fan	
id		AUC		pAUC
0		0.539607	0.492435
2		0.721866	0.554171
4		0.622098	0.527072
6		0.72277		0.529961
Average		0.651585	0.52591

pump	
id		AUC		pAUC
0		0.670769	0.57269
2		0.609369	0.58037
4		0.8886		0.676842
6		0.734902	0.570175
Average		0.72591		0.600019

```

## Dependency
Can run this on **Ubuntu 16.04 LTS**, **18.04 LTS**, **Cent OS 7**, and **Windows 10**.

### Software packages
- p7zip-full
- Python == 3.6.5
- FFmpeg

### Python packages
- Keras                         == 2.1.6
- Keras-Applications            == 1.0.8
- Keras-Preprocessing           == 1.0.5
- matplotlib                    == 3.0.3
- numpy                         == 1.16.0
- PyYAML                        == 5.1
- scikit-learn                  == 0.20.2
- librosa                       == 0.6.0
- audioread                     == 2.1.5 (more)
- setuptools                    == 41.0.0
- tensorflow                    == 1.15.0
- tqdm                          == 4.23.4
