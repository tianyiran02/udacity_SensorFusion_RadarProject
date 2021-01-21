# udacity_SensorFusion_RadarProject

## Implementation steps for the 2D CFAR process
So basically there are following steps:

1. define the training, guarding cells.
2. loop through the data set, the 2-d cfar is like a sliding window move across the data set.
3. with each window, calculate the training summation, then gets the average.
4. add the average with offset to get the target threshold for cell-under-test.
5. determine the cut

## Selection of Training, Guard cells and offset.
Because there's only one valid target, I chsoe training sets size as 1/10 of the whole signal. And guarding sets are relatively small, around 1/10 of the training sets.

According to the result from first 1-D fft, the SNR is relatively strong. Therefore the offset chosen was 10 dB.

## Steps taken to suppress the non-thresholded cells at the edges.
Similar as machine learning (NN), sliding window can't fully works on edge area because missing points. I simply remove the edge area, making the tests region slightly smaller
than origin dataset. This will result in lost of detection range, but result is good enough...
