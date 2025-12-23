# CS370-Computer-Vision

This repository contains four mini-projects from CS370 (Computer Vision). Each project includes code, data, and the exported figures. Below is a concise description of the assignments and the outputs, with explanations inferred from the code that generated them.

## Project 1: Intro to Image Formation and Color

**Assignment overview**
- Q1 (`Project 1/Code/Q1.py`): Numpy warm-up (zero/random matrices, vector norms, dot product/angle, Euclidean distance, reshape).
- Q3 (`Project 1/Code/Q3.py`): Builds a 3x3 response matrix `R` from flashlight emission spectra `F` and sensor responses `S`, then solves for reflectance coefficients of turquoise/goldenrod by inverting `R`.
- Q4 (`Project 1/Code/Q4.py`): Gray-world white balance. The per-channel mean is forced toward neutral gray (128), then the image is rescaled and saved.

**Output figures**
- Gray-world correction result (left: input cast, right: corrected using channel mean scaling).
  
  ![Project 1 gray-world correction](Project%201/original%20vs%20color%20corrected.png)

## Project 2: Alignment and Demosaicing

**Assignment overview**
- Q1a (`Project 2/code/alignChannels.py`, `Project 2/code/evalAlignment.py`): Aligns randomly shifted RGB channels by searching shifts that minimize the angle between flattened channels. The eval script saves side-by-side input/aligned images.
- Prokudin-Gorskii (`Project 2/code/alignProkudin.py`): Splits historical plates into B/G/R, aligns B and R to G, and exports aligned color images.
- Demosaicing (`Project 2/code/demosaicImage.py`, `Project 2/code/evalDemosaicing.py`): 
  - Baseline fills missing values with the channel mean.
  - Nearest-neighbor fills using the closest Bayer samples.
- Pixel neighbor correlation (`Project 2/code/pixelNeighborPlot.py`): Scatter plots of each channel’s neighbor relationship to show local correlation used to motivate interpolation.

**Output figures**
- Q1a alignment examples (left: shifted input, right: aligned result).
  
  ![Q1a alignment 1](Project%202/code/Q1a_pic1.png)
  ![Q1a alignment 2](Project%202/code/Q1a_pic2.png)
  ![Q1a alignment 4](Project%202/code/Q1a_pic4.png)
  ![Q1a alignment 5](Project%202/code/Q1a_pic5.png)
  ![Q1a alignment 6](Project%202/code/Q1a_pic6.png)
  ![Q1a alignment 8](Project%202/code/Q1a_pic8.png)
  ![Q1a alignment 9](Project%202/code/Q1a_pic9.png)

- Prokudin-Gorskii aligned results (B/G/R plates aligned into a color image).
  
  ![Aligned 00125v](Project%202/output/prokudin-gorskii/00125v-aligned.png)
  ![Aligned 00149v](Project%202/output/prokudin-gorskii/00149v-aligned.png)
  ![Aligned 00153v](Project%202/output/prokudin-gorskii/00153v-aligned.png)
  ![Aligned 00351v](Project%202/output/prokudin-gorskii/00351v-aligned.png)
  ![Aligned 00398v](Project%202/output/prokudin-gorskii/00398v-aligned.png)
  ![Aligned 01112v](Project%202/output/prokudin-gorskii/01112v-aligned.png)

- Demosaicing outputs (baseline vs nearest-neighbor for each image). Baseline is smoother due to mean fill; NN preserves edges but can introduce blocky artifacts.
  
  ![Cat baseline](Project%202/output/demosaic/cat-baseline-dmsc.png)
  ![Cat nn](Project%202/output/demosaic/cat-nn-dmsc.png)
  ![Pencils baseline](Project%202/output/demosaic/pencils-baseline-dmsc.png)
  ![Pencils nn](Project%202/output/demosaic/pencils-nn-dmsc.png)
  ![Puppy baseline](Project%202/output/demosaic/puppy-baseline-dmsc.png)
  ![Puppy nn](Project%202/output/demosaic/puppy-nn-dmsc.png)
  ![Squirrel baseline](Project%202/output/demosaic/squirrel-baseline-dmsc.png)
  ![Squirrel nn](Project%202/output/demosaic/squirrel-nn-dmsc.png)

- Pixel neighbor scatter plots (demonstrates strong local correlation within channels).
  
  ![Red channel neighbor scatter](Project%202/output/scatter-plot/red_channel_neighbor.png)
  ![RGB neighbor comparison](Project%202/output/scatter-plot/RGB-neighbor%20comparison.png)

## Project 3: Contrast, Denoising, and Hybrid Images

**Assignment overview**
- Contrast enhancement (`Project 3/initial/improve_im_contrast.py`): 
  - Contrast stretching spreads intensities to full [0,255].
  - Gamma correction applies `I_out = (I/255)^r * 255`.
  - Histogram equalization remaps intensities using the CDF.
- Denoising (`Project 3/initial/Denoising.py`): Compares Gaussian and median filters across multiple scales on Gaussian noise vs. pepper noise.
- Hybrid images (`Project 3/initial/vis_hybrid_image.py`): Combines low-frequency content from one image with high-frequency content from another to create a chimera effect.

**Output figures**
- Contrast stretching: images and their PDF/CDF plots before/after stretching.
  
  ![Stretching comparison image](Project%203/Output/stretching%20comparision%20image.png)
  ![Stretching PDF/CDF](Project%203/Output/stretching%20comparision%20pdf%20cdf.png)

- Gamma correction comparison (r=2 darkens, r=0.5 brightens).
  
  ![Gamma correction comparison](Project%203/Output/gamma%20correction%20comparison.png)

- Histogram equalization: PDF/CDF and visual comparison (equalized image has more uniform intensity distribution).
  
  ![CDF equalized comparison](Project%203/Output/cdf%20equalized%20comparison.png)
  ![CDF equalized photo comparison](Project%203/Output/cdf%20equalized%20photo%20comparison.png)

- Denoising results (Gaussian filter smooths Gaussian noise; median filter better suppresses pepper noise).
  
  ![Gaussian noise Gaussian filter](Project%203/Output/Q2/Gausian%20Noise%20Gausian%20Filter.png)
  ![Gaussian noise median filter](Project%203/Output/Q2/Gausian%20Noise%20Median%20Filter.png)
  ![Pepper noise Gaussian filter](Project%203/Output/Q2/Pepper%20Noise%20Gaussian%20Filter.png)
  ![Pepper noise median filter](Project%203/Output/Q2/Pepper%20Noise%20Median%20Filter.png)

- Hybrid images (low-pass + high-pass composition; details sharpen/blur depending on viewing distance).
  
  ![Cat and Dog chimera](Project%203/Output/Q3/Cat%20and%20Dog%20chimera.png)
  ![Cat and Dog chimera reversed](Project%203/Output/Q3/Cat%20and%20Dog%20chimera%20reversed.png)
  ![Sam and Jotaro](Project%203/Output/Q3/Sam%20and%20Jotaro.png)

## Project 4: Gradients, Orientation Histograms, and Corners

**Assignment overview**
- Gradients and orientation histogram (`Project 4/code/ImageGradientAndOrientationHistogram.py`):
  - Computes x/y gradients with `[-1, 0, 1]`, magnitude, and arctan orientation.
  - Bins orientations into 9 angle ranges and visualizes magnitude/orientation before and after Gaussian smoothing.
- Corner detection (`Project 4/code/detectCorners.py`, `Project 4/code/testCornerDetector.py`):
  - Simple score: local intensity change, squared and smoothed.
  - Harris score: second-moment matrix with `k=0.04`, followed by NMS.

**Output figures**
- Gradient magnitude and orientation (raw and Gaussian-smoothed). The Gaussian-smoothed outputs suppress noise while preserving dominant edge directions.
  
  ![Parrot gradient magnitude](Project%204/Ouput/parotGradient.png)
  ![Parrot gradient orientation](Project%204/Ouput/Angle.png)
  ![Parrot gradient magnitude (Gaussian)](Project%204/Ouput/parotGradientGaussian.png)
  ![Parrot gradient orientation (Gaussian)](Project%204/Ouput/Angle%20with%20Gaussian.png)
  ![Parrot gradient magnitude + orientation](Project%204/Ouput/parotGradientAng.png)
  ![Parrot gradient magnitude + orientation (Gaussian)](Project%204/Ouput/parotGradientGaussianAng.png)

- Corner detection examples (simple vs Harris; Harris tends to be more selective around true corners).
  
  ![Simple corners](Project%204/latex/figs/checker_simple_corner.png)
  ![Harris corners](Project%204/latex/figs/checker_harris.png)
