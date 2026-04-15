# Building tek-injector

tek-injector must be built in [MSYS2](https://www.msys2.org/), preferably with [TEK-X86_64 environment](https://github.com/teknology-hub/MinGW-env) that is tuned for building TEK software.

## 1. Install requirements

```sh
pacman -S base-devel git mingw-w64-tek-x86_64-toolchain
```

## 2. Get source code

Clone this repository:
```sh
git clone https://github.com/teknology-hub/tek-injector.git
cd tek-injector
```
, or download a point release e.g.
```sh
wcurl https://github.com/teknology-hub/tek-injector/releases/download/vX.Y.Z/tek-injector-X.Y.Z.tar.gz`
tar -xzf tek-injector-X.Y.Z.tar.gz
cd tek-injector-X.Y.Z
```

## 3. Setup build directory

At this stage you can set various build options, which are described in [Meson documentation](https://mesonbuild.com/Commands.html#setup). Release builds use the following setup:
```sh
CXXFLAGS="-gcodeview" LDFLAGS="-static -Wl,--pdb=" meson setup build --buildtype debugoptimized --default-library=both --default-both-libraries=static -Db_lto=true -Db_lto_mode=thin -Db_ndebug=true
```

## 4. Compile and install the project

```sh
meson install -C build
```
This will produce and install the binaries to `/tek-x86_64/bin`, library files to `/tek-x86_64/lib`, and install the header to `/tek-x86_64/include`.
