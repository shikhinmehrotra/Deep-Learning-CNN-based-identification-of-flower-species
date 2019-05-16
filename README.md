# Deep-Learning-CNN-based-identification-of-flower-species
In this project, Convolutional Neural Networks (CNNs) are used to predict whether a given image is that of a daisy or a rose. This project also contains a lot of image pre-processing techniques and data augmentation techniques.

# Data set
The data set consists of a directory of images of roses and daisies, with images of each type contained in sub-directories of the same name.

# Image augmentation and pre-processing

## Thresholding
Taking all the pixels whose intensities are above a certain threshold, and converting them to ones; the pixels having value less than the threshold are converted to zero. This results in a binary image.

## Erosion, dilation, opening and closing
Erosion shrinks bright regions and enlarges dark regions. 
Dilation shrinks dark regions and enlarges the bright regions.
Opening is erosion followed by dilation. Opening can remove small bright spots (i.e. “salt”) and connect small dark cracks. This tends to “open” up dark gaps between bright features.
Closing is dilation followed by erosion. Closing can remove small dark spots (i.e. “pepper”) and connect small bright cracks. This tends to “close” up dark gaps between bright features.

These are implemented using skimage.morphology module.

## Normalisation
Normalisation is carried out by using three methods. 
1) dividing all the pixel values of the image by 255
2) min-max normalisation
3) percentile based normalisation using the formula: image - (5th percentile of pixel values)/(95th percentile of pixel values - 5th percentile of pixel values)

## Augmentations
To augment the existing data set, linear and affine transformations are applied on the exisiting data set.

# Model building

## Custom data generator
A custom Keras data generator is built for customizability. It carries out some data pre-processing steps, and returns the batch of images as the pair X, y where X is of shape (batch_size, height, width, channels) and y is of shape (batch size, ).

## Ablation experiments
Running some experiments first to check whether the net is fitting on a small dataset or not by trying to fit the net on only a few images and just one epoch. 

## Overfitting on the training data
The model is first overfitted to the training data to see the goodness of fit and to check if it can learn well enough from a small dataset.

## Hyperparameter tuning

Hyperparameter Tuning
Following hyperparameters are tuned:
1) Learning Rate & Variation + Optimisers
2) Augmentation Techniques
The validation loss is tracked with increasing epochs for various values of a hyperparameter.

## Evaluating the final model
The final model is run and gives an AUC score of 91.1%.
