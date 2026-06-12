---
title: "Internet not working"
date: 2012-09-05
forum: Networking &amp; Wireless
---

### Post by snowlizard31 on 2012-09-05
I installed wubi on my win7 pc but i can't connect to the internet through wifi or ethernet cable. I have a broadcom 802.11 netword adapter 

iwconfig:

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:  off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit :7   RTS thr: off   Fragment thr : off
          Power Management: on
          
eth0      no wireless extensions.

---

### Post by cortman on 2012-09-05
> **snowlizard31 said:**
> I installed wubi on my win7 pc but i can't connect to the internet through wifi or ethernet cable. I have a broadcom 802.11 netword adapter 

iwconfig:

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID :off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit :7   RTS thr: off   Fragment thr : off
          Power Management: on
          
eth0      no wireless extensions.

What is the output of

```
lspci
```

---

### Post by snowlizard31 on 2012-09-05
lspic:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV630 [Mobility Radeon HD 2600 XT]
03:00.0 FireWire (IEEE 1394): LSI Corporation FW643 PCI Express 1394b Controller (PHY/Link) (rev 06)
04:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 05)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)

---

### Post by cortman on 2012-09-05
Try the instructions given [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx").

---

### Post by snowlizard31 on 2012-09-06
I've managed to install fakeroot and dkms properly but im having a problem with bcnwl can someone help me?

```

make.log:
DKMS make.log for bcmwl-5.60.48.36+bdcom for kernel 3.2.0-29-generic-pae (i686)
Thu Sep  6 15:36:02 PDT 2012
make: Entering directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
  LD      /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/shared/linux_osl.o
In file included from /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/shared/linux_osl.c:19:0:
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/include/linuxver.h:23:28: fatal error: linux/autoconf.h: No such file or directory
compilation terminated.
make[1]: *** [/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/shared/linux_osl.o] Error 1
make: *** [_module_/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic-pae'



snowlizard@ubuntu:~/Desktop$ sudo dpkg -i fakeroot*
[sudo] password for snowlizard: 
Selecting previously unselected package fakeroot.
(Reading database ... 141118 files and directories currently installed.)
Unpacking fakeroot (from fakeroot_1.18.4-2_i386.deb) ...
Setting up fakeroot (1.18.4-2) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Processing triggers for man-db ...
snowlizard@ubuntu:~/Desktop$ sudo dpkg -i bcmwl*
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 141155 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb) ...
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-29-generic-pae
Building for architecture i686
Building initial module for 3.2.0-29-generic-pae
ERROR (dkms apport): kernel package linux-headers-3.2.0-29-generic-pae is not supported
Error! Bad return status for module build on kernel: 3.2.0-29-generic-pae (i686)
Consult /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic-pae
Warning: No support for locale: en_US.utf8
snowlizard@ubuntu:~/Desktop$ sudo apt-get install linux-headers-$snowlizard
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'linux-headers' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



```

---

### Post by snowlizard31 on 2012-09-07
Nevermind I just deleted generic-pea and reinstalled it and got it to work that way

---

