# chntpw for Windows
The source code is from https://pogostick.net/~pnh/ntpasswd/. It is adapted to build with MinGW-w64. Check `Makefile` before you run `make`. Current `Makefile` builds so-callled 64-bit Windows executables only. If you want 32-bit version, you need to install the correct toolchain and set the correct `CC` variable in `Makefile`.

Code in this repo were successfully built on Fedora 36. Before building I installed:
```shell
sudo dnf install mingw64-gcc mingw64-gcc-c++  mingw64-openssl-static mingw64-winpthreads-static
```

I alse added `#include <stdint.h>` in `ntreg.h` because the compiler complained about unknown type `int32_t`.

## Why for Windows?
The original author did provide prebuilt bootable disk image as well as linux executables. But he claimed he could not handle bitlocked devices. There is workaround though, that you boot into a Windows PE and unlock bitlocked disks with `manage-bde` with the correct key or password. Then pass `C:\Windows\Sytem32\config\SAM` to `chntpw`.

Of course you have to obtain the key or password legally. Keep in mind **I am not attempting to teach you how to crack the bitlocker at all**. Anyway, if bitlocker were to be compromised that easy then it made no sense for such technology or even TPM to exist.