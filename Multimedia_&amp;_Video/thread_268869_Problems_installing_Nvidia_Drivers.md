---
title: "Problems installing Nvidia Drivers"
date: 2006-09-30
forum: Multimedia &amp; Video
---

### Post by fatsheep on 2006-09-30
I already have the Nvidia drivers installed (installed them with automatix) but I just realized that they are very out of date so I went to the Nvidia website to install the latest ones.  When I try to install the AMD64 NVIDIA drivers I get this error message:

>  ERROR: An NVIDIA kernel module 'nvidia' appears to already be loaded in your
         kernel.  This may be because it is in use (for example, by the X
         server), but may also happen if your kernel was configured without
         support for module unloading.  Please be sure you have exited X
         before attempting to upgrade your driver.  If you have exited X, know
         that your kernel supports module unloading, and still receive this
         message, then an error may have occured that has corrupted the NVIDIA
         kernel module's usage count; the simplest remedy is to reboot your
         computer.


Followed by this error message:

> 
  ERROR: Installation has failed.  Please see the file
         '/var/log/nvidia-installer.log' for details.  You may find
         suggestions on fixing installation problems in the README available
         on the Linux driver download page at [www.nvidia.com](www.nvidia.com).


Here's the contents of /var/log/nvidia-installer.log:

> creation time: Sat Sep 30 20:45:18 2006

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
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
ERROR: An NVIDIA kernel module 'nvidia' appears to already be loaded in your
       kernel.  This may be because it is in use (for example, by the X
       server), but may also happen if your kernel was configured without
       support for module unloading.  Please be sure you have exited X before
       attempting to upgrade your driver.  If you have exited X, know that your
       kernel supports module unloading, and still receive this message, then
       an error may have occured that has corrupted the NVIDIA kernel module's
       usage count; the simplest remedy is to reboot your computer.


Help?

---

### Post by tseliot on 2006-10-01
Try Envy (follow the instructions on the website):
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

