---
title: "NVIDIA 9600GT driver Wont Install"
date: 2010-09-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Spade12 on 2010-09-08
Hey guys, I took the plunge and upgraded from 10.04 to 10.10 beta and consequently my video card is no longer recognized and manual and synaptic aided installs do not work. 

Trying from terminal I get an error:

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue Sep  7 17:52:02 2010
installer version: 256.53

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  compat32 install chroot : (not specified)
  compat32 install prefix : (not specified)
  compat32 install libdir : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 256.53.
-> There appears to already be a driver installed on your system (version: 195.
   36.24).  As part of installing this driver (version: 256.53), the existing d
   river will be uninstalled.  Are you sure you want to continue? ('no' will ab
   ort installation) (Answer: Yes)
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> The CC version check failed:
   
   Could not compile 'gcc-version-check.c'.  Please be  sure you have your Linu
   x distribution's gcc  and libc development packages installed.
   
   If you know what you are doing and want to ignore the gcc version check, sel
   ect "No" to continue installation.  Otherwise, select "Yes" to abort install
   ation, set the CC environment variable to the name of the compiler used to c
   ompile your kernel, and restart installation.  Abort now? (Answer: No)
-> Kernel source path: '/lib/modules/2.6.35-20-generic/build'
-> Kernel output path: '/lib/modules/2.6.35-20-generic/build'
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
       driver download page at www.nvidia.com.
```

Heres my launchpad link : [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/632797](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/632797)

---

### Post by jppr on 2010-09-08
First... Remove in Synaptic Nvidia-current driver, then install Bleachbit and clean up your system - > boot and install again Nvidia-current -> and boot again ;)

Edit. Or... do fresh daily-build live-cd installation [http://cdimage.ubuntu.com/daily-live/20100908/](http://cdimage.ubuntu.com/daily-live/20100908/) and it is sure that system works = )
I have Nvidia 9400 Gt card and did just fresh installation, system works fine = )

---

