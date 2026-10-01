# CMB_spectral_distortions
code to provide numerical estimates for the minimum observation time required to constrain the mu-spectral distortions of the CMB below the fiducial value from lambda-CDM

foreground models are taken from  https://doi.org/10.1093/mnras/stx1653

## Tuning instrumental parameters, fiducial foreground parameters
fiducial parameters are listed at the beginning of the paper, one can change the instrumental specifications (frequency range, total etendue, bandwidth and so on) as well as the fiducial foreground parameter models by changing the values in these cells.

the foreground models can be changed by changing the details of the functions num_phot_sig(...) and calc_full_spectrum(...). 

To get the code to compile easily with a new foreground model the following changes must be made:

1. n_params_fg, n_signals_fg must reflect the total number of free parameters and the number of foregrounds being considered
2. params = [...] this array must be updated to reflect the new parameter set
(this also means changes in num_phot_sig(..) and calc_full_spectrum while unpacking the array and defining values of the foreground parameters in the functions)
3. the new foreground signal (if any) should be added to the full_spectrum signal in calc_full_spectrum(...)
4. a new elif(signal_index==new_signal_index)... must be added in num_phot_sig(...)
