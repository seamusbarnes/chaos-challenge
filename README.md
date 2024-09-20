# CHAOS Challenge

CHAOS -> Combined (CT-MR) Healthy Abdominal Organ Segmentation Challenge Datta

The chaos challenge can be found here: https://chaos.grand-challenge.org/

CT dataset: 20 training and 20 test cases
MRI dataset: 20 training and 20 test cases with T1-Dual and T2 SPIR sequences

Training set:

- CHAOS_Train_Sets.zip
- 890.8 MB

Test set:

- CHAOS_Test_Sets.zip
- 1.1 GB

Filetypes:

- .dcm -> from DICOM (Digital Imaging and Communications in Medicine), technical standard for digital storage and transmission of medical images
- .nrrd -> "nearly raw raster data", file format for representation and processing of n-dimensional raster data

## What is here

The script `build_chaos_dataset.py` converts the dataset as given by the organizers to another of medical images.
As given, the dataset consists of single dicom files, which have anonimized dicom files, which all have different
InstanceUIDs making these hard to read with standard tools. Run the script for the usage.

## MRI

For the T1 sequence, the separation of the in-phase and
out-phase image is done using the echo time from the dicom header. Next to that the masks are given als PNG files.
This tool converts these to a new mask format with the following values:

`
MAPPING = {
    0: 'background',
    1: 'liver',
    2: 'right kidney',
    3: 'left kidney',
    4: 'spleen'
}`
![MRI example](mri_example.png?raw=true?s=200 "MRI Example read with ITK-SNAP")

## For CT

The masks are converted in a `.nrrd` file where 1 is the liver, and 0 the background.
![CT example](ct_example.png?raw=true?s=200 "CT Example read with ITK-SNAP")

## What is needed

- Python 3.6
- SimpleITK >= 1.2
- tqdm
- Pillow
- numpy
