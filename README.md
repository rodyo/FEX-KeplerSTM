[![View Kepler State Transition Matrix (MEX) on File Exchange](https://www.mathworks.com/matlabcentral/images/matlab-file-exchange.svg)](https://www.mathworks.com/matlabcentral/fileexchange/26349-kepler-state-transition-matrix-mex)

[![Donate to Rody](https://i.stack.imgur.com/bneea.png)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=4M7RMVNMKAXXQ&source=url)

# FEX-KeplerSTM

The Kepler State transition matrix provides a way to progress any given state vector for a given time step, without having to perform a lengthy triple-coordinate conversion (from Cartesian coordinates to Kepler elements, progressing, and back). This procedure has been generalized and greatly optimized for computational efficiency by Shepperd (1985)[1], who
used continued fractions to calculate the corresponding solution to Kepler's equation. The resulting algorithm is an order of magnitude faster that mentioned triple coordinate conversion, which makes it very well suited as a basis for a number of other algorithms that require frequent progressing of state vectors.
This procedure implements a robust version of this algorithm. A small correction to the original version was made: instead of Newton's method to update the Kepler-loop, a Halley-step is used. This change makes the algorithm much more robust while increasing the rate of convergence even further. If the algorithm fails however (which SHOULD never occur), the slower triple-coordinate conversion is automatically started.
Both a M-version and a C++-version have been included in this submission. The C++ version can be compiled by issuing
mex progress_orbit.c

at the MATLAB command prompt (when in the correct directory). After compiling (let me know what goes wrong) you can run a small demo (test_STM.m) which will produce something similar to the screenshot on top here; a plot of the factor by which the MEX version outperforms the M-version. On my computer this was 5.5 times faster on average, sometimes peaking to no less than 260 times faster.

References:
[1] S.W. Shepperd, "Universal Keplerian State Transition Matrix". Celestial Mechanics 35(1985) pp. 129--144, DOI: 0008-8714/85.15

If you find this work useful, please consider [a donation](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=4M7RMVNMKAXXQ&source=url).
