---
title: "trouble installing nforce audio drivers"
date: 2006-06-21
forum: Multimedia &amp; Video
---

### Post by jptvelo on 2006-06-21
Hi all,

I'm having trouble getting sound to work. I'm unable to successfully run nvidia's nforce driver installer. So far I've installed the kernel source, headers, libc6-headers, and it still complains about missing "stuff". The current error is:
ERROR:
       If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.

       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the appropriate nvidia-installer command line option.

I'm running 2.6.15-23-amd64-generic. I haven't compiled it myself (do I need to?), but like I said, I've got the source and header packages, seems to me that's all I should need? Here's my list of relevant installed packages:

linux-amd64-generic
linux-image-2.6.15-23-amd64-generic linux-image-amd64-generic
linux-restricted-modules-2.6.15-23-amd64-generic
linux-restricted-modules-amd64-generic linux-restricted-modules-common
linux-source-2.6.15 

I'm sure that whatever I'm missing is pretty simple; I mean this shouldn't be that hard, right?
Here's the full nvidia-nforce-installer.log output, obtained with the following command-line options:
--kernel-source-path=/usr/src/linux-source-2.6.15/ --kernel-output-path=/lib/modules/2.6.15-23-amd64-generic/



nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Wed Jun 21 13:48:33 2006

option status:
  license pre-accepted      : false
  expert                    : false
  uninstall                 : false
  driver info               : false
  no precompiled interface  : false
  no ncurses color          : false
  no questions              : false
  silent                    : false
  Installer install prefix  : /usr
  kernel source path        : /usr/src/linux-source-2.6.15/
  net kernel install path   : (not specified)
  audio kernel install path : (not specified)
  proc mount point          : /proc
  ui                        : (not specified)
  tmpdir                    : /tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA audio driver for Linux-x86_64
-> Found package NVIDIA network driver for Linux-x86_64
-> Please select packages for installation:
   Selections:
   NVIDIA audio driver for Linux-x86_64 (1.0-7)
-> Starting install of NVIDIA audio driver for Linux-x86_64
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> License accepted.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.15-23-amd64-generic (buildd@yellow) (gcc
   version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Tue May 23 13:45:47
   UTC 2006
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Using the kernel source path '/usr/src/linux-source-2.6.15/' as specified by
   the '--kernel-source-path' commandline option.
-> Kernel source path: '/usr/src/linux-source-2.6.15/'
-> Using the kernel output path '/lib/modules/2.6.15-23-amd64-generic/' as
   specified by the '--kernel-output-path' commandline option.
-> Kernel output path: '/lib/modules/2.6.15-23-amd64-generic/'
-> Performing cc_version_check with CC="cc".
ERROR:
       If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.

       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the appropriate nvidia-installer command line option.
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by BerlinOliver on 2006-07-26
HI,

I have similiar problems. 

Try to install the linux-headers. than the installer should run correctly. but you have to edit the modules after that. That's my problem at the moment. because I can't find /etc/modules.conf or /etc/modprobe.conf.
(Have a look in :
/usr/share/doc/nforce/ReleaseNotes.html)

---

