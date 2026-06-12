---
title: "Wireless driver installed but not working correctly."
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by s0fa on 2009-11-20
I installed Ubuntu 9.10 on an Acer Aspire One D250, which has a Broadcom 4312 rev 01 mini-pcie wireless network adapter. According to Broadcom the 4312 is one of their cards supported by the in-house Broadcom Linux driver. Ubuntu can install this in the system>administration>hardware drivers menu and as of right now this is how I have installed it. The light still does not come on and wicd does not display any wireless networks. iwconfig shows only my wired internet (eth0) and Local Loopback (lo) whatever that is.

 I have also tried to install the driver using tutorials which outline how to install it via console input, but have run into errors that say that I do not have the correct privileges to compile the driver once it's been untarred. Following another tutorial I tried to increase my privileges by adding sudo chmod 666 /dev/nul to my rc.local file to no avail. 

 I have blacklisted the bcm43xx, b43, b43legacy, ssb, ath_pci, and ath_hal drivers because tutorials suggested that they may interfere. 

I am new to Linux, I've tried to find my answers among tutorials online but I have not yet been able to solve my problem and so I'm asking you the community what I am doing wrong.

---

### Post by dca on 2009-11-20
If you can't compile and it references permissions you need to preface the commands 'make' & 'make install' with *sudo*
 
 
sudo make install
 
I can't think of anything else that would need to be done besides installing the 'build-essential' meta-packge from the repositories which gives you gcc and bunch of others to assist in compiling...

---

### Post by s0fa on 2009-11-23
So I have been trying to install the driver manually following the readme Broadcom has to go alongside their driver. 

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

When I "make" the driver I get this output.
 
~/Downloads/hybrid_wl$ make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  LD      /home/someone/Downloads/hybrid_wl/built-in.o
  CC [M]  /home/someone/Downloads/hybrid_wl/src/wl/sys/wl_linux.o
  CC [M]  /home/someone/Downloads/hybrid_wl/src/wl/sys/wl_iw.o
  CC [M] /home/someone/Downloads/hybrid_wl/src/shared/linux_osl.o
  LD [M]  /home/somone/Downloads/hybrid_wl/wl.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/someone/Downloads/hybrid_wl/wl.o
see include/linux/module.h for more information
  CC      /home/someone/Downloads/hybrid_wl/wl.mod.o
  LD [M]  /home/someone/Downloads/hybrid_wl/wl.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'

someone@somewhere:~/Downloads/hybrid_wl$ sudo modprobe lib80211
[sudo] password for someone: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
someone@somewhere:~/Downloads/hybrid_wl$ sudo insmod wl.ko
insmod: error inserting 'wl.ko': -1 Unknown symbol in module

---

