# Linear Regression Benchmark Results 

## Summary
```
   Results below show the performance comparison of linear regression with MXNet vs Keras-Tensorflow using sparse tensors
```                                                   

### Results
### Inference Benchmark
#### Input samples are sparse feature vectors with 10,000 dimensions
### Configuration
| Dataset          | Synthetic(Randomly generated)                                |
| :--------------- | :----------------------------------------------------------- |
| Keras            | v2.2.4                                                      |
| TensorFlow       | v1.11.0                                                     |
| MXNet-mkl         | v1.3.0   

#### CPU
##### Speed
| Instance Type | GPUs  | Batch Size  | Keras-MXNet (Samples/Sec) | Keras-TensorFlow (Samples/Sec)  |
|-----|-----|-----|-----|-----|
| C5.8XLarge |   0  | 64  | 71K | 77K
| C5.8XLarge |   0  | 128 | 111K | 143K
| C5.8XLarge |   0  | 256 | 166K | 200K
| C5.8XLarge |   0  | 512 | 250K | 250K
| C5.8XLarge |   0  | 1024 | 333K | 333K

#### Memory Consumed
| Instance Type | GPUs  | Batch Size | Keras-MXNet (MB) | Keras-TensorFlow (MB)  |
|-----|-----|-----|-----|-----|
| C5.8XLarge |   0  | 64  | 1630.8 | 1573.8 |
| C5.8XLarge |   0  | 128 | 1574.7 | 1561.2 | 
| C5.8XLarge |   0  | 256 | 1477.8 | 1501.4  |
| C5.8XLarge |   0  | 512 | 1407.0| 1472.5 |
| C5.8XLarge |   0  | 1024 | 1336.3 | 1466.8 |

#### GPU
### Configuration
##### Input samples are sparse feature vectors with 10,000 dimensions
| Dataset          | Synthetic(Randomly generated)                                |
| :--------------- | :----------------------------------------------------------- |
| Keras            | v2.2.4                                                      |
| TensorFlow-GPU   | v1.11.0                                                     |
| MXNet-cu90mkl    | v1.3.0                                                      |

##### Single GPU
##### Speed
| Instance Type | GPUs  | Batch Size  | Keras-MXNet (Samples/Sec) | Keras-TensorFlow (Samples/Sec)  |
|-----|-----|-----|-----|-----|
| P3.8XLarge |   1  | 64  | 33K | 50K
| P3.8XLarge |   1  | 128 | 43K | 83K 
| P3.8XLarge |   1  | 256 | 83K | 143K
| P3.8XLarge |   1  | 512 | 125K | 200K
| P3.8XLarge |   1  | 1024 |250K | 250K

##### GPU Utilization
| Instance Type | GPUs  | Batch Size | Keras-MXNet (GPU Utilization %) | Keras-TensorFlow (GPU Utilization %)  |
|-----|-----|-----|-----|-----|
| P3.8XLarge |   1  | 64  | 9 | 7
| P3.8XLarge |   1  | 128 | 8 | 7
| P3.8XLarge |   1  | 256 | 8 | 7
| P3.8XLarge |   1  | 512 | 8 | 7
| P3.8XLarge |   1  | 1024 | 7 | 8

##### GPU Memory Consumed
| Instance Type | GPUs  | Batch Size | Keras-MXNet (GPU Memory (MB)) | Keras-TensorFlow (GPU Memory (MB))  |
|-----|-----|-----|-----|-----|
| P3.8XLarge |   1  | 64  | 966.7 | 16135.5
| P3.8XLarge |   1  | 128 | 970.9 | 16135.5
| P3.8XLarge |   1  | 256 | 973.1 | 16135.5
| P3.8XLarge |   1  | 512 | 994.1 | 16135.5
| P3.8XLarge |   1  | 1024 | 987.7 | 16135.5

### Note
Run the file as `python run_sparse_benchmark.py`, by default the benchmark runs for `training` with `10 epochs` and batch size of `512`
Inference results have been rounded to the nearest 1000th value and in the above numbers, `K` represents `1000`, so `1K=1000`

### References
MXNet supports sparse data in 2 NDArray formats - CSRNDArray and RowSparseNDArray which are defined in `mxnet.ndarray.sparse` package
For further details on MXNet Sparse NDArray API check [documentation related to MXNet Sparse](https://mxnet.incubator.apache.org/api/python/ndarray/sparse.html)

Keras Input layer supports sparse data by setting a boolean placeholder value - check document for [Keras Input layer](https://keras.io/layers/core/#input)
