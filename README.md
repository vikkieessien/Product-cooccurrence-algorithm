# Product Co-occurrence Algorithm

Memory-efficient product co-occurrence algorithm in Python 
and incremental data ingestion pipeline using Apache Spark.

## What this project covers

### Assignment 1 — Product Co-occurrence Algorithm
Computes how often pairs of products are bought together 
in the same basket from a large sales dataset.

The main challenge was processing the data without loading 
it all into memory at once. I solved this using a chunk-based 
hashing approach, splitting pairs across chunks using 
`smaller product id % number of chunks` so every pair gets 
counted exactly once.

### Assignment 2 — Incremental Ingestion with Apache Spark
Reads multiple sales files incrementally, removes duplicate 
basket and product combinations and saves the clean result 
as Parquet format.

## Tools
- Python 3
- Apache Spark / PySpark
- gzip
- csv

## How to run

Generate test data:
```
python generate_data.py --scale 1
```

Run Assignment 1:
```python
results = run_assignment1('data_1.csv.gz', num_chunks=4)
```

Run Assignment 2:
```python
result = incremental_ingestion(
    input_files=['file_1.csv.gz', 'file_2.csv.gz'],
    output_path='output/deduplicated_data'
)
```
