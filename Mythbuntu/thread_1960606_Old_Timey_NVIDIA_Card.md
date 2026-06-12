---
title: "Old Timey NVIDIA Card"
date: 2012-04-17
forum: Mythbuntu
---

### Post by mattneub on 2012-04-17
Just installed 11.10 on an older machine, and everything is working nicely except the video drivers.  This is likely because my card is really old, GeForce 5200, *I would get a better one but the interface is AGP so my options are limited.*

Anyway, I've tried all four of the NVIDIA driver options availbale in the Additional Drivers dialog (96, 96+updates, 173, and 173+updates), and none of them seem to recognize my card properly, all say the below on the X Server Display Configuration Screen in the NVIDIA X Server Settings progaram and TV out, from the card's S-Video port, is not operational.

[B]Unable to load X Server Display Configuration page:

Failed to query NoScanout for screen 0.[/B]

Attempted to load older drivers from the NVIDIA site, but unsuccessful, below is the log file from my attempted install.

Just curious if anyone has handled this one before and has any ideas.

NVIDIA Installer Log:
-> License accepted.
-> Installing NVIDIA driver version 173.14.27.
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation 
   anyway? (Answer: Yes)
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/3.0.0-17-generic/build'
-> Kernel output path: '/lib/modules/3.0.0-17-generic/build'
ERROR: If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.
       
       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the equivalent nvidia-installer command line option.
       
       Depending on where and how the kernel sources (or the
       kernel headers) were installed, you may need to specify
       their location with the SYSSRC environment variable or
       the equivalent nvidia-installer command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by klc5555 on 2012-04-17
Sounds like you have to install the kernel source, the headers, or provide the path to the source for NVidia's installer to compile from.

Using NVidia's own installer in Ubuntu is a real pain and in general not recommended. However, Ubuntu's wiki does have a guide for it that may not be completely out of date: [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

