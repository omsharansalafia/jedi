# JEDI
## Gamma-ray burst *je*t structure *di*stributions from jet propagation and breakout semi-analytical modeling

This repository contains the output of the semi-analytical calculations presented in Salafia, Barbieri, Ascenzi and Toffano (2020) - Astronomy & Astrophysics, Volume 636, id.A105, doi:10.1051/0004-6361/201936335 , arxiv:1907.07599

The repository contains two folders, LGRB and SGRB, containing the simulated populations of Long Gamma-Ray Bursts and Short Gamma-Ray Bursts respectively.

Each folder contains a series of hdf5 files, each containing a simulated population of jets. The naming convention is as follows:
- for LGRBs, the file name is long_Lxx.x_Tyy.y_thjz.zzz.hdf5, where xx.x is the base 10 logarithm of the center of the injected jet luminosity distirbution, in erg/s; yy.y is the center of the injection duration distribution in seconds; z.zzz is the jet opening angle at launch, in rad
- for SGRBs, the file name is short_Lxx.x_Tyy.y_thjz.zzz_tdu.uu.hdf5, where xx.x is the base 10 logarithm of the center of the injected jet luminosity distirbution, in erg/s; yy.y is the center of the injection duration distribution in seconds; z.zzz is the jet opening angle at launch, in rad; u.uu is the delay between merger and jet injection, in seconds.

Each hdf5 file contains the following elements:
- N_events: the number of jets in the synthetic population (int)
- thv_res: the number of logarithmically spaced viewing angles, between 0 and pi/2, at which the observed luminosity has been computed
- Gj: the terminal Lorentz factor of the jet material
- intrinsic_distributions/lum_0 : array of jet kinetic luminosities, in erg/s
- intrinsic_distributions/lum_cdf : cumulative probability distribution, evaluated at lum_0, from which the kinetic jet luminosities have been extracted to produce the population
- intrinsic_distributions/T_0 : array of jet injection durations, in s
- intrinsic_distributions/T_cdf : cumulative probability distribution, evaluated at T_0, from which the jet injection durations have been extracted to produce the population
- jets/Lj: array containing the N_events kinetic luminosities of the simulated jets
- jets/T: array containing the N_events injection durations of the simulated jets
- jets/thj: the opening angle of the jets at launch, in rad
- jets/thv: matrix of shape (N_events,thv_res). Each row refers to a different jet, and contains the viewing angles, in radians, at which the observed luminosities and energies have been computed
- jets/thv: matrix of shape (N_events,thv_res). Each row contains the isotropic-equivalent gamma-ray energy, in erg, received by an observer at the corresponding viewing angle (given in the previous matrix), assuming 100% efficiency of kinetic-to-radiative energy conversion 
- jets/E_cocoon: array of length N_events. Each element refers to a different jet, and represents the energy stored in the cocoon, in erg, at the time of jet breakout
- jets/M_cocoon: array of length N_events. Each element refers to a different jet, and represents the mass in the cocoon, in grams, at the time of jet breakout
- jets/G_cocoon: array of length N_events. Each element refers to a different jet, and represents the cocoon maximum terminal Lorentz factor G_cocoon = 1 + E_cocoon/M_cocoon c^2
- jets/theta_cocoon: array of length N_events. Each element refers to a different jet, and represents the angular scale, in rad, of the cocoon (see the paper for a description of how the cocoon structure is defined and computed)
- jets/E_jet: array of length N_events. Each element refers to a different jet, and represents the total injected jet energy, in erg, minus that spent in breaking out
- jets/T_GRB: array of length N_events. Each element refers to a different jet, and represents the jet duration after breakout, in seconds

The subfolder jets/structures contains N_events subfolders called jetD, where D is an integer number running from 0 to N_events-1. Each subfolder contains the jet and cocoon structures defined as follows:
- th_j: an array of angles in radians, at which the jet structure is evaluated
- dEdO_j: array of jet kinetic energies per unit steradians, in erg/sr, evaluated at th_j
- G_j: array of jet Lorentz factors, evaluated at th_j
- th_c: an array of angles in radians, at which the cocoon structure is evaluated
- dEdO_c: array of cocoon kinetic energies per unit steradians, in erg/sr, evaluated at th_c
- G_c: array of cocoon Lorentz factors, evaluated at th_c







