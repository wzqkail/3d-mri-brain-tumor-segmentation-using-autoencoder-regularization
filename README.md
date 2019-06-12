# 3D MRI Brain Tumor Segmentation Using Autoencoder Regularization

[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/3d-mri-brain-tumor-segmentation-using/brain-tumor-segmentation-on-brats-2018)](https://paperswithcode.com/sota/brain-tumor-segmentation-on-brats-2018?p=3d-mri-brain-tumor-segmentation-using)
![Keras](https://img.shields.io/badge/Implemented%20in-Keras-red.svg)

![The model architecture](https://www.suyogjadhav.com/images/misc/brats2018_sota_model.png)
<center><b>The Model Architecture</b></center><br /><center>Source: https://arxiv.org/pdf/1810.11654.pdf</center>
<br /><br />

Keras implementation of the paper <b>3D MRI brain tumor segmentation using autoencoder regularization</b> by Myronenko A. (https://arxiv.org/abs/1810.11654). The author (team name: <b>NVDLMED</b>) ranked #1 on the <a href="https://www.med.upenn.edu/sbia/brats2018/" target="_blank">BraTS 2018</a> leaderboard using the model described in the paper.

This repository contains the model complete with the loss function, all implemented end-to-end in Keras. The usage is described in the next section.

# Usage
1. Download the file [`model.py`](model.py) and keep in the same folder as your project notebook/script.

2. In your python script, import `build_model` function from `model.py`.

   ```python
   from model import build_model
   ```

   It will automatically download an additional script needed for the implementation, [`group_norm.py`](https://github.com/titu1994/Keras-Group-Normalization/blob/master/group_norm.py), which contains keras implementation for the group normalization layer.

3. Note that the input MRI scans you are going to feed need to have 4 dimensions, with <b>channels-first</b> format. i.e., the shape should look like (c, H, W, D), where:
- `c`, the no.of channels are divisible by 4.
- `H`, `W`, `D`, which are height, width and depth, respectively, are _all_ divisible by 2<sup>4</sup>, i.e., 16.
 This is to get correct output shape according to the model.

4. Now to create the model, simply run:

   ```python
   model = build_model(input_shape, output_channels)
   ```

   where, `input_shape` is a 4-tuple (channels, Height, Width, Depth) and `output_channels` is the no. of channels in the output of the model.
   The output of the model will be the segmentation map generated by the model with the shape (output_channels, Height, Width, Depth), where Height, Width and Depth will same as that of the input.

# Issues

If you encounter any issue or have a feedback, don't hesitate to [raise an issue](https://github.com/IAmSuyogJadhav/3d-mri-brain-tumor-segmentation-using-autoencoder-regularization/issues/new).

# Updates
- Thanks to [@doc78](https://github.com/doc78) , the NaN loss problem has been permanently fixed.
- The NaN loss problem has now been fixed (clipping the activations for now).
- Added an argument in the `build_model` function to allow for different no. of channels in the output.
