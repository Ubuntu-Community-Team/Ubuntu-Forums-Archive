---
title: "Problem getting to work wireless modem in HP2140"
date: 2013-05-14
forum: Networking &amp; Wireless
---

### Post by zeitus on 2013-05-14
Hello everyone

I am trying to get to work the modem in a HP2140 after installing lubuntu 12.04 . I am following the steps given in here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

They basically tell you to uncompress the .tar.gz file and the type make clean and the make install when I do that I get:

rodrigo@HP-2140:~/modem$ make clean
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd` clean
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic'
Wireless Extension is the only possible API for this kernel version
Using Wireless Extension API
  CLEAN   /home/rodrigo/modem/.tmp_versions
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'
rodrigo@HP-2140:~/modem$ make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic'
Wireless Extension is the only possible API for this kernel version
Using Wireless Extension API
  LD      /home/rodrigo/modem/built-in.o
  CC [M]  /home/rodrigo/modem/src/shared/linux_osl.o
  CC [M]  /home/rodrigo/modem/src/wl/sys/wl_linux.o
/home/rodrigo/modem/src/wl/sys/wl_linux.c:388:2: error: unknown field 'ndo_set_multicast_list' specified in initializer
/home/rodrigo/modem/src/wl/sys/wl_linux.c:388:2: warning: initialization from incompatible pointer type [enabled by default]
/home/rodrigo/modem/src/wl/sys/wl_linux.c:388:2: warning: (near initialization for 'wl_netdev_ops.ndo_validate_addr') [enabled by default]
make[2]: *** [/home/rodrigo/modem/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/home/rodrigo/modem] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'
make: *** [all] Error 2


also in their readme file ([http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt))  they claim that:
"

PRECOMPILED DRIVER-------------------Some distros (Ubuntu and Fedora at the least) already have a version ofthis driver in their repositories precompiled, tested and ready to go.You just use the package manager to install the proper package.  Ifits available for your distro, this is usually an easier solution. Seethe end of this document for further discussion."

Any ideas where I can find this precompiled version?

Many thanks for any help you can provide,

---

### Post by Hadaka on 2013-05-14
Hi, that driver is already built into the 12.04 version,
if you have a wired connection, please open a terminal
ctrl/alt/t and do..

```
sudo apt-get install bcmwl-kernel-source
modprobe wl
```
thanks

---

### Post by zeitus on 2013-05-14
Hello Hadaka

Thanks for suggestion. The problem is that I don't have a wired connection either... :(

---

### Post by Hadaka on 2013-05-14
Hi,Lets take a look at what your wireless card is
to verify which driver you need. Please COPY and 
paste the following into a terminal..

```
lspci -n | grep 0280 
```

since you have no connection, we'll make this easy,
all i need from the output is the [14e4:XXXX] so
please post that.
thanks.

---

