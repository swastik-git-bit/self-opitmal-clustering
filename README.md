Self-Optimal Clustering (SOC) for Image Segmentation

Project Overview

This repository contains a Python-based implementation and comparative analysis of the Self-Optimal Clustering (SOC) technique, an advanced version of the Improved Mountain Clustering (IMC) algorithm originally proposed by Verma and Roy (2014).

The SOC algorithm replaces heuristic threshold constraints with a mathematically optimized threshold function computed via Lagrange's interpolation polynomial. By iteratively refining a per-cluster scaling factor ($\beta_m$), the algorithm maximizes the Global Silhouette Index (GSI), achieving superior compactness within clusters and separability between them.

Key Features

Data-Driven Optimization: Uses Lagrange interpolation rather than heuristic guessing to determine optimal cluster boundaries.

3D Hyperspace Normalization: Processes RGB image pixels as 3-dimensional feature vectors normalized into a unit hypercube.

Automated Model Selection: Evaluates multiple cluster counts ($k$) and automatically selects the optimum based on GSI maximization.

Pre-Processing Pipeline: Includes proportional aspect-ratio scaling and Gaussian spatial smoothing to mitigate high-frequency visual noise.

Quantitative Impact & Results

The algorithm was benchmarked against traditional models (K-means, FCM, EM, K-medoid) and heuristic mountain models (IMC-1, IMC-2) across diverse image datasets (40,000 feature vectors per test).

Superior Accuracy: Achieved a peak GSI of 0.8765 (at optimal $k=2$), outperforming traditional K-means (0.8528) and baseline IMC models.

Cluster Density: Reduced the Partition Index (PI) by 21.4% versus K-means, resulting in significantly tighter cluster bounds and maximizing the Dunn Index to 1.0453.

Conditional Convergence: Successfully proved threshold convergence by the 9th iteration in stress-test scenarios.

🛠️ Installation

Clone this repository:

git clone [https://github.com/yourusername/self-optimal-clustering.git](https://github.com/yourusername/self-optimal-clustering.git)
cd self-optimal-clustering


Install the required dependencies:

pip install -r requirements.txt


Usage

Run the main pipeline script. The program will prompt you to enter a direct URL to an image and your desired number of clusters ($k$).

python main.py


Example Inputs:

Image URL: https://upload.wikimedia.org/wikipedia/commons/thumb/8/85/Selena_Gomez_-_Walmart_Soundcheck_concert.jpg/320px-Selena_Gomez_-_Walmart_Soundcheck_concert.jpg

No. of clusters required: 2

The script will output the progression of the Lagrange optimization to the console, print the final GSI scores, and launch a Matplotlib window displaying a $2 \times 3$ grid comparing the original image with the SOC, IMC-1, and IMC-2 segmented outputs.

Repository Structure

main.py - The main execution pipeline, including image preprocessing, model execution, and visualization.

clustering_core.py - (Add your factorcal, soc, imc2, and lagrangepoly functions here)

requirements.txt - Project dependencies.

notebooks/ - Contains Jupyter notebooks for generating data visualizations and graphs used in the final report.
