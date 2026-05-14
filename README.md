# Sampling library

Using: OpenFOAM-13

This folder contains the probes-related part of `src/sampling`.

## Local changes

Changed files copied from the local OpenFOAM-13:

- `probes/probes.C`
- `probes/probes.H`

The change adds `probes::distribute(const polyDistributionMap&)` and re-finds fixed probe locations after mesh redistribution.

The function object is registered as `myprobes` so it can be loaded from `libmysampling.so` without colliding with the standard `probes` function object.

The supporting files in `probes/` are included because they are part of the same probes function-object implementation and build target.

## Build note

`Make/files` is trimmed to the custom probes sources and targets `$(FOAM_USER_LIBBIN)/libmysampling.so` instead of `$(FOAM_USER_LIBBIN)/libsampling.so` to avoid conflict with the original sampling library.
