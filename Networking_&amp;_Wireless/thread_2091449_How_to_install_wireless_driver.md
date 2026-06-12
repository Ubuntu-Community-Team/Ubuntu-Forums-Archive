---
title: "How to install wireless driver?"
date: 2012-12-05
forum: Networking &amp; Wireless
---

### Post by intercept on 2012-12-05
I'm quite new at this, so I'm having pretty elementary problems, I think. I need some help. I don't know how to properly use the 'make' command here.

Trying to install the driver for this PCI card. 
[http://www.asus.com/Networks/Wireless_Adapters/PCEN10/](http://www.asus.com/Networks/Wireless_Adapters/PCEN10/)

After downloading, the readme says:

```

You can enter top-level directory of driver and execute follwing command to
Compile, Installation, or uninstall the driver:

        1. Change to Super User
	   sudo su

	2. Compile driver from the source code 
	   make

	3. Install the driver to the kernel
           make install
           reboot

	4. uninstall driver
	   make uninstall

```

When I try to do that, it doesn't work.

```
adam@adam-PORTEGE-R705:~/Documents/Linux$ ls
firmware  readme.txt    rtllib     wpa_supplicant-0.6.9
HAL       realtek       runwpa     wpa_supplicant-0.6.9.tar.gz
Makefile  release_note  wpa1.conf
adam@adam-PORTEGE-R705:~/Documents/Linux$ make
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-17-generic'
gcc: error: /lib/modules/3.5.0-17-generic/build/include/linux/autoconf.h: No such file or directory
gcc: fatal error: no input files
compilation terminated.
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/adam/Documents/Linux/HAL/rtl8192/Makefile". Fix it to use ccflags-y.  Stop.
make[1]: *** [_module_/home/adam/Documents/Linux/HAL/rtl8192] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-17-generic'
make: *** [all] Error 2
adam@adam-PORTEGE-R705:~/Documents/Linux$ 

```

Your help's greatly appreciated.

---

### Post by chili555 on 2012-12-05
> gcc: error: /lib/modules/3.5.0-17-generic/build/include/linux/autoconf.h: No such file or directory
gcc: fatal error: no input files
compilation terminated.This suggests you don't have the needed build tools installed:```
sudo apt-get install build-essential
```And this little gem:> scripts/Makefile.build:49: *** CFLAGS was changed in "/home/adam/Documents/Linux/HAL/rtl8192/Makefile". Fix it to use ccflags-y.  Stop...suggests you are trying to build a driver built for an older kernel version that is incompatible with your shiny new 3.5.0-xx kernel. From the included readme.txt:>  --This driver supports RealTek rtl8192CE/8188CE PCI Wireless LAN NIC for

     **2.6 kernel**:
     Fedora Core, Debian, Mandriva, Open SUSE, Gentoo, 
     Ubuntu 7.10/8.04/8.10/9.04/9.10/10.04/10.10, 
     moblin(V2), android-x86_090916, etc.

     **2.4 kernel**:
     Redhat 9.0/9.1I believe rtl8192ce is included by default. Did it not work for you? Please run and post:```
lspci -nn | grep 0280
```Thanks.

---

