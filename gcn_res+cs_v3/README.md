# GCN_res-CS-v3
This is an improvement of the  [(GCN_res + C&S_v2)](https://github.com/ytchx1999/GCN_res-CS-v2)  model, using the C&amp;S method. **This is the v3 version.** Here I only use the validation label in the post-processing steps of Label Propagation（LP）, and the validation label information is not used in the training for gradient descent, which can also be seen from the number of parameters. 

### ogbn-arxiv

+ Check out the model：[(GCN_res + C&S_v2)](https://github.com/ytchx1999/GCN_res-CS-v2)

+ Check out the C&S method：[C&S](https://arxiv.org/abs/2010.13993)

#### Environmental Requirements

+ pytorch == 1.7.1
+ pytorch_geometric == 1.6.3
+ ogb == 1.2.4

#### Experiment Setup：

The model is 8 layers, 10 runs which conclude 500 epochs.

```bash
python gcn_res_cs.py
```

#### Detailed Hyperparameter:

```bash
num_layers = 8
hidden_dim = 128
dropout = 0.5
lr = 0.01
runs = 10
epochs = 500
alpha = 0.2
beta = 0.7
num_correction_layers = 50
correction_alpha = 0.7
num_smoothing_layers = 50
smoothing_alpha = 0.7
scale = 1.
A1 = 'DAD'
A2 = 'DAD'
```

#### Result:

```bash
All runs:
Highest Train: 98.15 ± 0.01
Highest Valid: 73.61 ± 0.21
  Final Train: 98.15 ± 0.01
   Final Test: 73.91 ± 0.14
```

| Model            | Test Accuracy   | Valid Accuracy  | Parameters | Hardware        |
| ---------------- | --------------- | --------------- | ---------- | --------------- |
| GCN_res + C&S_v3 | 0.7391 ± 0.0014 | 0.7361 ± 0.0021 | 155824     | Tesla T4 (16GB) |

