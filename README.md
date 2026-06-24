# Automatic Measurements of Fishes physical traits (version 2).

<code style="color" : red">**Note:**</code> This digital tool was developed in connection to the [INDUCE](https://meerwissen.org/partnership-projects/induce/) project (2020-2022), as part of the [MeerWissen](https://meerwissen.org) (African-German Partners for Ocean Knowledge) initiative. The tool was developed by Ciodaro Guerra under the supervision of Ago Merico and Sonia Bejarano.

![](sample_fish.PNG)
--------------------------------------------------------------


Create a Python software to automatically measure fish's traits given a photo.

There are two modes of operation. 

+ Give to the script the reference length. The name of the picture should contain the TL (Total Lenght in physical dimensions, cm, in, etc.) of the fish, with the tag "TL". With that number, the software computes the transformation from pixels to cm, inches, etc. If an error occurs, the distances will be shown in pixels. example of correctly formatted picture name: S schlegeli 15.7 SL-18.8 TL.jpg
+ Specify that there is reference tape in the picture.

The fish should be placed Horizontally with the mouth pointing to the left.
Use the script ```manualPreProcessing.py``` to perform rotations and flipping:

```
Execute on terminal. It shows the image, and it waits
for user input:
    -v : Vertical axis flip
    -h : Horizontal axis flip
    -c : clockwise rotation
    -cc: counter clockwise rotation. 
```

You could also put on the name of the file el keyword '.R.' so that vertical
flipping occurs. If your image has height bigger than width. 
the script will rotate counter-clockwise and perform the flipping by if name has '.R.'

The general parameters:

```
parser.add_argument("--path_pictures", help="path to pictures. return CNN feature detection")
parser.add_argument("--mode_ratio", help="in_name_TL, reference_tape")
parser.add_argument("--path_template", help="if mode_ratio=reference_tape, pass the path to the template")
parser.add_argument("--length", help="if mode_ratio=reference_tape, pass physical distante of tape")
parser.add_argument("--show_detection", help="return CNN feature detection")
parser.add_argument("--show_end_result", help="return image with dimension drawing")
parser.add_argument("--debug", help="show inline prints")
parser.add_argument("--contrast", help="select number between 1.0 and 3.0")
```
## Installation
- clone the repository
- Create two folders, bin and build_graph. Place yolov2.weights in "build_graph" replace bin. Download them here [here](https://drive.google.com/drive/folders/1pQPy27n-dhk3vybnUfKYfaJhle3zZbMY)
- conda create -n AMT_v2 python=3.6
- conda install -c anaconda tensorflow-gpu==1.15
- conda install -c conda-forge opencv==4.2.0
- conda install -c anaconda cython==0.29.14
- python setup.py build_ext --inplace
- pip install .
- pip install matplotlib==3.1.2
- pip install pandas==1.0.5

on  ```fish_training``` you can find the images and annotation used to train the
yolo. Visit ```sample_images``` to check some images and .csv results. 

Relies on darkflow. Inference is configured to be done with CPU. (Python 3.6). To setup (Tested on ubunto 16):

--------------------------------------------------------------

+ **Notebooks/exploratory.ipynb:** jupyter notebook with a demo.
+ **fish_detector.py:** isolated python script to measure fish's traits.
+ **Classes/:** Set of python classes to help fish_detector.py



** Still under development***


