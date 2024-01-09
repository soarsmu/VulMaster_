# VulMaster_


This repository is the replication package of **"Out of Sight, Out of Mind: Better Automatic Vulnerability Repair by Broadening Input Ranges and Sources"**.


## Resources

* In the replication, we provide:
  * the scripts we used to:
    * `0a_train.sh`: fine-tune the models with validation.
    * `0b_infer.sh`:  perform inference using the fine-tuned models.
  * the source code we used to:
    * `train_model.py`: the main code for training/validating.
    * `test_model.py`: the main code for testing.
    * `src/`: the utils, model, data preprocessing, etc. for FiD.
  * the CWE knowledge we collected from CWE website:
    * `CWE_examples_GPT35_generate_fixes_full.csv`: the raw vulnerable code examples and their analysis and CWE names directly collected from CWE homepages.
    * `chatgpt_api_generate_fix.py`: the main code for generating fixes for vulnerable code examples with expert analysis as guidance.
    * `ChatGPT_generated_fixes_labels.xlsx`: the manually labeled correctness for generated fixes for vulnerable code examples.
   
      
 [Here](https://drive.google.com/drive/folders/1L5fkJ_J-NvuWlcr-GbfomorxoS6HwuTs?usp=sharing) is CodeT5 model after adaptation. Please download it and rename it into './bugfix_pretrain_with_ast/pytorch_model.bin' and put it in the root dir.
 
* `requirements.txt` contains the dependencies needed.

* The experiments were conducted on a server equipped with NVIDIA L40 GPU and Intel(R) Xeon(R) CPU E5-2420 v2@ 2.20GHz, running the Ubuntu OS.
  
* If you meet OutOfMemoryError: please note that you typically need around 30 GB GPU memory to run VulMaster.



## Install dependencies


Please install them first.
```
unzip VulMaster-main.zip
cd VulMaster-main
cd VulMaster-main
conda create -n vulmaster python=3.8 
conda activate vulmaster
pip install -r requirements.txt
```
## Train and Test 

To replicate VulMaster, ensure that `c_dataset/` is in the root path of this project. 

Training:
```
bash 0a_train.sh 
```

Testing:
```
bash 0b_infer.sh
```

Compute metrics:
```
pip install --upgrade tree-sitter
python calculate_metrics_all_models
```


## Generate fixes for CWE vulnerable code examples via ChatGPT
```
python chatgpt_api_generate_fix.py
```

