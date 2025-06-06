# MIMXRT633S Peripheral Access Crate

[![no-std](https://github.com/OpenDevicePartnership/mimxrt633s-pac/actions/workflows/nostd.yml/badge.svg)](https://github.com/OpenDevicePartnership/mimxrt633s-pac/actions/workflows/nostd.yml)
[![check](https://github.com/OpenDevicePartnership/mimxrt633s-pac/actions/workflows/check.yml/badge.svg)](https://github.com/OpenDevicePartnership/mimxrt633s-pac/actions/workflows/check.yml)
[![crates.io](https://img.shields.io/crates/v/mimxrt633s-pac.svg)](https://crates.io/crates/mimxrt633s-pac)
[![Documentation](https://docs.rs/mimxrt633s-pac/badge.svg)](https://docs.rs/mimxrt633s-pac)
[![LICENSE](https://img.shields.io/badge/License-MIT-blue)](./LICENSE)

This crate provides an autogenerated API for access to NXP MIMXRT633s
peripherals. The API is generated using
[svd2rust](https://github.com/rust-embedded/svd2rust).

## Regenerating the PAC

On a unix-style OS, all you need are these commands:

```console
$ svdtools patch patch/MIMXRT633S.yaml
$ svd2rust -i svd/MIMXRT633S.svd.patched --reexport-interrupt --ignore-groups --impl-defmt defmt --impl-debug --impl-debug-feature debug
$ rm -r src/*
$ form -i lib.rs -o src
$ rm lib.rs
$ cargo fmt
```

On windows you need to replace the `/` with `\` and additionally run
`dos2unix` to convert the line endings, like so:

```console
$ svdtools.exe patch patch/MIMXRT633S.yaml
$ svd2rust.exe -i svd\MIMXRT633S.svd.patched --reexport-interrupt --ignore-groups --impl-defmt defmt --impl-debug --impl-debug-feature debug
$ rm -r src\*
$ form -i lib.rs -o src
$ rm lib.rs
$ cargo fmt
$ cd src
$ dos2unix **\*.rs *.rs
```
