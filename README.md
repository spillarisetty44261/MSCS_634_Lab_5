# MSCS 634 – Lab 5: Hierarchical and DBSCAN Clustering

## Purpose
This lab applies two clustering algorithms, Agglomerative Hierarchical Clustering and DBSCAN, to the Wine dataset from scikit-learn. The goal is to see how each algorithm groups the data, how its parameters affect the results, and how well the clusters match the real wine types using the Silhouette, Homogeneity and Completeness scores.

## Key Insights
- **Standardization was necessary** because the features have very different scales (for example, `proline` is in the hundreds to thousands while `hue` is below 2).
- **Hierarchical clustering with 3 clusters worked best.** It had the highest silhouette score (0.277) and homogeneity and completeness of about 0.79. The dendrogram also showed three clearly separated branches.
- **DBSCAN found only 2 clusters.** The best setting (eps = 2.4, min_samples = 5) gave homogeneity 0.504 and completeness 0.552, and marked 36 wines as noise. Two of the wine types are too close together for DBSCAN to separate them.
- **Parameter choice mattered a lot for DBSCAN.** A small eps turned most points into noise, and a large eps merged everything into one cluster. Only a narrow range of values gave useful results.

## Challenges and Decisions
- **Plotting 13 features:** I used PCA to reduce the data to 2 dimensions for the scatter plots only. The clustering itself used all 13 standardized features.
- **Choosing DBSCAN parameters:** I tested several combinations of eps and min_samples and picked the one with the best homogeneity and completeness that still found more than one cluster.
- **Silhouette with noise:** the silhouette score for DBSCAN was calculated without the noise points. This makes DBSCAN's score look a bit better than it really is, which I note in the analysis.
