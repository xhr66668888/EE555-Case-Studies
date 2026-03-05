Haoran Xu
hx666

1. MCA (Degree=MS, Track=Cyber)
Use G table in html. I use first 3 dims to make 3D point.
MS and Cyber are active categories, so final point is center of these 2 category coordinates in 3D.
Write this clearly in paper: x = (g_MS + g_Cyber)/2.
From table: g_MS(D1,D2,D3)=(-2,0,-1), g_Cyber(D1,D2,D3)=(0,-1,2).
Final 3D vector = ((-2+0)/2, (0-1)/2, (-1+2)/2) = (-1, -0.5, 0.5).

2. Autoencoder design (mixed data)
Input dim = 7 (Degree one-hot 2 + Track one-hot 3 + q1 q2 numeric 2).
I design 7 -> 5 -> 3 -> 5 -> 7.
Encoder hidden ReLU, bottleneck linear (or tanh), decoder hidden ReLU.
Output is group-wise: Degree(2) softmax, Track(3) softmax, q1 q2 linear.
Loss = CE(Degree) + CE(Track) + MSE(q1,q2), weighted sum.

3. Scaling choice
Notebook selected scaler: robust.
Reason: distribution has outlier and some skew, robust is more stable than standard/minmax in this dataset.
So I choose RobustScaler.

4. Clustering model selection (Part 1 and Part 2)
Part 1 Manual 6D: K-Means best k=3, GMM best k=3.
Part 2 AE 6D: K-Means best k=3, GMM best k=3.
K-Means (k=3): FM train=1.0, test=1.0.
GMM (k=3): FM train=1.0, test=1.0.
So k=3 is consistent with WCSS/Silhouette and AIC/BIC + cluster-vs-profile table.

5. Which feature extraction better
Manual 6D and AE 6D both very good for K-Means and GMM (FM almost perfect).
But HDBSCAN shows Part 1 train FM=0.9855, Part 2 train FM=1.0 (test both 1.0).
So AE 6D is slightly better and more stable.
t-SNE also shows good separation, AE embedding is cleaner.

What to submit
Single PDF only (as activity says).
Inside PDF: answer 1-5.
Name and id on top page.

Haoran Xu
hx666
