# Introduction #
YOLO2TrainingManager is a Python script tool to wrap [YOLO2](https://pjreddie.com/darknet/yolo/) training data and enviorment. It saves all data needed for a training and all data generated by the training in the same folder. It makes you easier to manage numerous training tasks.       

# Configuration #
1. To rename GlobalConfig.ini.example to GlobalConfig.ini
2. To modify YOLO\_ROOT\_PATH and JOB\_ROOT\_PATH in GlobalConfig.ini

> YOLO\_ROOT\_PATH is the path of YOLO2 source code.

> JOB\_ROOT\_PATH is the path of job folder to save all training data and enviorment.

Both of YOLO\_ROOT\_PATH and JOB\_ROOT\_PATH support absolute and relative path. They are relative to the location of Manager.py 

# Usage #
Usage: Manager.py <detector/classifier> [OPTION]

-c, --cmd &nbsp;&nbsp;&nbsp; **command: train, recall, report**

-i, --id &nbsp;&nbsp;&nbsp; **task ID**

-d, --data_cfg &nbsp;&nbsp;&nbsp; **the path of training data cfg file, for example, cfg/voc.data**

-n, --net_cfg &nbsp;&nbsp;&nbsp; **the path of network cfg file, for example, cfg/yolo9000.cfg** 

-w, --weight &nbsp;&nbsp;&nbsp; **weight file** 

All options support absolute and relative path. They are relative to YOLO\_ROOT\_PATH

# Use Case 1 #
To start a new training: Python Manager.py <detector/classifier> -c train -d cfg/voc.data -n yolo-voc.cfg

# Use Case 2 #
To start a fine-tuned training with a pre-trained weight: Python Manager.py <detector/classifier> -c train -d cfg/voc.data -n yolo-voc.cfg -w yolo.weights

# Use Case 3 #
To resume a training: Python Manager.py <detector/classifier> -c train -i 20170604194957193

> "20170604194957193" is the ID of the training task you want to resume. You can find it in the job folder.

# Tree of job folder #
```
.
|-- 20170604194957193
|   |-- backup
|   |   |-- tiny-yolo-voc-64-8-001_100.weights
|   |   `-- tiny-yolo-voc-64-8-001_200.weights
|   |-- cfg
|   |   |-- tiny-yolo-voc-64-8-001.cfg
|   |   |-- union-eg.data
|   |   `-- voc-eg.names
|   |-- PathSetting.json
|   |-- train_data
|   |   |-- 2007_test.txt
|   |   `-- train_union.txt
|   |-- train.run
|   `-- yolo
|       |-- cfg
|       |-- darknet
|       |-- data
|       |-- .git
|       |-- .gitignore
|       |-- LICENSE
|       |-- Makefile
|       |-- obj
|       |-- README.md
|       |-- results
|       |-- scripts
|       `-- src
`-- 20170604203612931
    |-- backup
    |   `-- yolo-voc_100.weights
    |-- cfg
    |   |-- voc.data
    |   |-- voc.names
    |   `-- yolo-voc.cfg
    |-- PathSetting.json
    |-- train_data
    |   |-- 2007_val.txt
    |   `-- train.all.txt
    |-- train.run
    `-- yolo
        |-- backup
        |-- cfg
        |-- darknet
        |-- data
        |-- .git
        |-- .gitignore
        |-- LICENSE
        |-- Makefile
        |-- obj
        |-- README.md
        |-- results
        |-- scripts
        `-- src