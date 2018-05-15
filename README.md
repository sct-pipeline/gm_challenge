![](https://github.com/neuropoly/gm_challenge/blob/master/doc/logo_challenge.png)

# Gray Matter Challenge (2018)
Spinal cord gray matter imaging challenge for the 5th Spinal Cord Workshop (June 22<sup>nd</sup>, Paris).

### Getting started

The objective for this challenge is to propose a protocol that will generate the best image quality. The script `WMGM.py` will execute commands for Spinal Cord Toolbox (SCT) to process the data and compute metrics for assessing the quality of the image. For more details, please see: https://goo.gl/2owcL7.

Two NIfTI files are required: an initial scan and a re-scan without repositioning.

##### Dependencies

- [Spinal Cord Toolbox (SCT)](https://github.com/neuropoly/spinalcordtoolbox)

SCT is used for all processing of the data.
(2 files are uploaded)

---
### Processing

- The second image is registered to the first in order to compute the SNR using the two-image subtraction method.

- The spinal cord and gray matter of each image are segmented automatically.

- White matter segmentation is generated by subtracting the gray matter segmentation from the cord segmentation.

---
### Analysis
Three different metrics are used to evaluate the imaages:

#### Signal-to-noise ratio (SNR):
  The SNR is computed with SCT using the two-image subtraction method.

#### Contrast:
The mean signal is computed in the white matter and gray matter of image 1. The contrast is then computed according to the following equation:

Contrast = abs(mean(WM) - mean(GM)) / min{mean(WM),mean(GM)}

#### Sharpness:
The Laplacian is first calculated for image 1. The mean of the Laplacian inside the cord is then computed to give the measure of sharpness for the image.

