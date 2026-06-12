---
title: "NFORCE-Linux-x86-1.0-0306"
date: 2005-11-20
forum: Multimedia &amp; Video
---

### Post by Tobias_at_ch on 2005-11-20
My Nforce3 chip set has lockups if I want to run 3D and wireless network.
after google search i would like to install the NFORCE patch 1.0-0306 from  officel Nvidia site.
However i got error messages. Before i apply the patch I do 
CC=gcc-3.3 and export CC

can anyone help?

Ubuntu-breezy 5.10
2.6.12-9-386

&#65279;nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Sun Nov 20 12:54:37 2005

option status:
  license pre-accepted      : false
  expert                    : false
  uninstall                 : false
  driver info               : false
  no precompiled interface  : true
  no ncurses color          : false
  no questions              : false
  silent                    : false
  Installer install prefix  : /usr
  kernel source path        : /usr/src/linux-headers-2.6.12-9
  net kernel install path   : (not specified)
  audio kernel install path : (not specified)
  proc mount point          : /proc
  ui                        : (not specified)
  tmpdir                    : /tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA network driver for Linux-x86
-> Found package NVIDIA audio driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA network driver for Linux-x86 (1.0-12)
   NVIDIA audio driver for Linux-x86 (1.0-6)
-> Starting install of NVIDIA network driver for Linux-x86
-> Checking for loaded module nvnet
-> Checking for loaded module forcedeth
-> License accepted.
-> Skipping check for conflicting rpms.
-> Not probing for precompiled kernel interfaces.
-> Using the kernel source path '/usr/src/linux-headers-2.6.12-9' as specified
   by the '--kernel-source-path' commandline option.
-> Kernel source path: '/usr/src/linux-headers-2.6.12-9'
-> Kernel output path: '/lib/modules/2.6.12-9-386/build'
-> Performing cc_version_check with CC="gcc-3.3".
-> running command /bin/grep "^PATCHLEVEL ="
   /usr/src/linux-headers-2.6.12-9/Makefile | /usr/bin/cut -d " " -f 3
-> Kernel module filename is nvnet.ko
   Cleaning kernel module build directory.
   executing: 'cd ./nvnet; make clean'...
   rm -f *.ko *mod.* *.cmd nvenet.o nvenetif.o nvnet.o *~ core
-> Building kernel module:
   executing: 'cd ./nvnet; make module SYSSRC=/usr/src/linux-headers-2.6.12-9 S
   YSOUT=/lib/modules/2.6.12-9-386/build'...
   make -C /lib/modules/2.6.12-9-386/build		\
   KBUILD_SRC=/usr/src/linux-headers-2.6.12-9	     KBUILD_VERBOSE=1	\
   KBUILD_CHECK= KBUILD_EXTMOD="/tmp/selfgz17173/NFORCE-Linux-x86-1.0-0306-pkg1
   /nvnet"	\
           -f /usr/src/linux-headers-2.6.12-9/Makefile modules
   /bin/sh: /usr/src/linux-headers-2.6.12-9/scripts/gcc-version.sh: file or        
   directory not found	
   mkdir -p /tmp/selfgz17173/NFORCE-Linux-x86-1.0-0306-pkg1/nvnet/.tmp_versions
   make -f /usr/src/linux-headers-2.6.12-9/scripts/Makefile.build obj=/tmp/self
   gz17173/NFORCE-Linux-x86-1.0-0306-pkg1/nvnet
   make[4]: /usr/src/linux-headers-2.6.12-9/scripts/Makefile.build: file or     
   directory not found	
   make[4]: *** no rule, to make »/usr/src/linux-headers-2.6.12-9/scripts/Makef
   ile.build« finish.
   make[3]: *** [_module_/tmp/selfgz17173/NFORCE-Linux-x86-1.0-0306-pkg1/nvnet] 
   error 2
   make[2]: *** [modules] error 2
-> Error.
ERROR: The NVIDIA kernel module was not created.
ERROR: Installation of the network driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at [www.nvidia.com](www.nvidia.com).
-> Starting install of NVIDIA audio driver for Linux-x86
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> License not accepted, aborting installation of audio driver.

 lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
0000:00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev f6)
0000:00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
0000:00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
0000:00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
0000:00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
0000:00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
0000:00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 031b (rev a1)
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Gigabit Ethernet 10/100/1000Base-T Adapter (rev 13)
0000:02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ab)
0000:02:01.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ab)
0000:02:01.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 03)
0000:02:01.3 System peripheral: Ricoh Co Ltd: Unknown device 0576 (rev 01)
0000:02:01.4 System peripheral: Ricoh Co Ltd: Unknown device 0592
0000:02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by ubuntu_demon on 2005-11-20
I moved this thread. Please don't post questions in the customization section!

---

### Post by Tobias_at_ch on 2005-11-21
I did so, apt-get update / apt-get upgrade there is no update needed.

somehow it looks that it can not find some files and directory in /usr/src/linux-headers-2.6.12-9

"/usr/src/linux-headers-2.6.12-9/scripts/gcc-version.sh: file or directory not found"

that's all I have in there, why he wants to find this gcc-version.sh

/usr/src/linux-headers-2.6.12-9/scripts$ ls -l
insgesamt 24
drwxr-xr-x  2 root root 4096 2005-11-10 19:24 basic
drwxr-xr-x  2 root root 4096 2005-11-10 19:24 genksyms
drwxr-xr-x  2 root root 4096 2005-11-10 19:24 kconfig
drwxr-xr-x  2 root root 4096 2005-11-10 19:24 lxdialog
-rw-r--r--  1 root root    0 1995-11-21 23:00 Makefile
drwxr-xr-x  2 root root 4096 2005-11-10 19:24 mod
drwxr-xr-x  2 root root 4096 2005-11-10 19:24 package

---

### Post by Teroedni on 2005-11-21
you run as root or sudo right??

also
ERROR: Installation of the network driver has failed. Please see the file
'/var/log/nvidia-nforce-installer.log' for details

could you post that log as it will expain better waht went wrong

---

### Post by Tobias_at_ch on 2005-11-22
this is the log file.....
i only tryed the network module

thank your


&#65279;nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Sun Nov 20 12:54:37 2005

option status:
license pre-accepted : false
expert : false
uninstall : false
driver info : false
no precompiled interface : true
no ncurses color : false
no questions : false
silent : false
Installer install prefix : /usr
kernel source path : /usr/src/linux-headers-2.6.12-9
net kernel install path : (not specified)
audio kernel install path : (not specified)
proc mount point : /proc
ui : (not specified)
tmpdir : /tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA network driver for Linux-x86
-> Found package NVIDIA audio driver for Linux-x86
-> Please select packages for installation:
Selections:
NVIDIA network driver for Linux-x86 (1.0-12)
NVIDIA audio driver for Linux-x86 (1.0-6)
-> Starting install of NVIDIA network driver for Linux-x86
-> Checking for loaded module nvnet
-> Checking for loaded module forcedeth
-> License accepted.
-> Skipping check for conflicting rpms.
-> Not probing for precompiled kernel interfaces.
-> Using the kernel source path '/usr/src/linux-headers-2.6.12-9' as specified
by the '--kernel-source-path' commandline option.
-> Kernel source path: '/usr/src/linux-headers-2.6.12-9'
-> Kernel output path: '/lib/modules/2.6.12-9-386/build'
-> Performing cc_version_check with CC="gcc-3.3".
-> running command /bin/grep "^PATCHLEVEL ="
/usr/src/linux-headers-2.6.12-9/Makefile | /usr/bin/cut -d " " -f 3
-> Kernel module filename is nvnet.ko
Cleaning kernel module build directory.
executing: 'cd ./nvnet; make clean'...
rm -f *.ko *mod.* *.cmd nvenet.o nvenetif.o nvnet.o *~ core
-> Building kernel module:
executing: 'cd ./nvnet; make module SYSSRC=/usr/src/linux-headers-2.6.12-9 S
YSOUT=/lib/modules/2.6.12-9-386/build'...
make -C /lib/modules/2.6.12-9-386/build \
KBUILD_SRC=/usr/src/linux-headers-2.6.12-9 KBUILD_VERBOSE=1 \
KBUILD_CHECK= KBUILD_EXTMOD="/tmp/selfgz17173/NFORCE-Linux-x86-1.0-0306-pkg1
/nvnet" \
-f /usr/src/linux-headers-2.6.12-9/Makefile modules
/bin/sh: /usr/src/linux-headers-2.6.12-9/scripts/gcc-version.sh: file or
directory not found
mkdir -p /tmp/selfgz17173/NFORCE-Linux-x86-1.0-0306-pkg1/nvnet/.tmp_versions
make -f /usr/src/linux-headers-2.6.12-9/scripts/Makefile.build obj=/tmp/self
gz17173/NFORCE-Linux-x86-1.0-0306-pkg1/nvnet
make[4]: /usr/src/linux-headers-2.6.12-9/scripts/Makefile.build: file or
directory not found
make[4]: *** no rule, to make »/usr/src/linux-headers-2.6.12-9/scripts/Makef
ile.build« finish.
make[3]: *** [_module_/tmp/selfgz17173/NFORCE-Linux-x86-1.0-0306-pkg1/nvnet]
error 2
make[2]: *** [modules] error 2
-> Error.
ERROR: The NVIDIA kernel module was not created.
ERROR: Installation of the network driver has failed. Please see the file
'/var/log/nvidia-nforce-installer.log' for details. You may find
suggestions on fixing installation problems in the README available on
the Linux driver download page at [www.nvidia.com](www.nvidia.com).
-> Starting install of NVIDIA audio driver for Linux-x86
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> License not accepted, aborting installation of audio driver.

---

### Post by Tobias_at_ch on 2005-11-26
with NVIDIA-Linux-x86-1.0-7676-pkg1 and the Nvidia Nforce Driver additional the "noapic" in the grub menu, seems to solve the problem, wireless network activated works now.

---

### Post by mo_x on 2005-11-26
You probably need to install linux-headers-2.6.12-9-386 to make the installer work.

---

