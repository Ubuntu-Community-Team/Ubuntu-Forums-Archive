---
title: "wlan doesnt work on acer aspire 3613lci 10.04"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by topias.l on 2010-05-10
The wireless doesn't work on my acer aspire 3610lci with ubuntu 10.04. I have installed to drivers trough ndiswrapper but i cant install acer_acpi. It shows this when i 'make' and 'sudo make install' the source:

topias@topias-laptop:~$ cd Wireless/acer_acpi-0.9.1
topias@topias-laptop:~/Wireless/acer_acpi-0.9.1$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/topias/Wireless/acer_acpi-0.9.1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/topias/Wireless/acer_acpi-0.9.1/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/topias/Wireless/acer_acpi-0.9.1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [acer_acpi.ko] Error 2
topias@topias-laptop:~/Wireless/acer_acpi-0.9.1$ sudo make install
[sudo] password for topias: 
make -C /lib/modules/`uname -r`/build SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [acer_acpi.ko] Error 2
topias@topias-laptop:~/Wireless/acer_acpi-0.9.1$ 

I would appreciate any answers, thanks.

---

