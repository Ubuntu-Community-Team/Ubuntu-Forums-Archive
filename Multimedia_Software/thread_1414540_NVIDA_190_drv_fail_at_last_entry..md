---
title: "NVIDA 190 drv fail at last entry."
date: 2010-02-23
forum: Multimedia Software
---

### Post by sandman3838 on 2010-02-23
Hello

Please check this out and let me know if you have any ideas or a better way to install this silly thing.  At the moment I'm using 185 drivers and I would not mind upgrading to 190 or even 195 versions of the driver.

My video card is a Nvidia 9800 GT  512mb.

1- Add repositories to ubuntu 9.04 and 9.10 karmic koala

- For ubuntu 9.10 karmic koala :

You have to add the repository using this command :

sudo add-apt-repository ppa:nvidia-vdpau/ppa


2- Now update or refresh the installation

sudo apt-get update

3- Install the driver :

sudo apt-get install nvidia-190-modaliases nvidia-glx-190  nvidia-settings-190

ERROR:

kevin@kj-Linux:~$ sudo apt-get install nvidia-190-modaliases nvidia-glx-190  nvidia-settings-190
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-190-modaliases is already the newest version.
nvidia-190-modaliases set to manually installed.
Package nvidia-settings-190 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  nvidia-settings
E: Package nvidia-settings-190 has no installation candidate


Any ideas?

---

### Post by sandman3838 on 2010-02-23
I tried this....

I went to the NVIDIA site directly an I downloaded the driver here are the results perhaps this will help?

I ran:
sudo NVIDIA-Linux-x86_64-190.53-pkg2.run

During the process it failed and it suggested I check out the log file that it created.

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue Feb 23 19:17:13 2010
installer version: 1.0.7

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
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '1705'
   of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       [www.nvidia.com](www.nvidia.com).
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

HERE is the README GUIDE IF IT MIGHT HELP?

[http://us.download.nvidia.com/XFree86/Linux-x86_64/190.53/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/190.53/README/index.html)

---

### Post by lidex on 2010-02-23
Follow this guide and just make sure to change the file names where needed to reflect the correct driver:
[http://ubuntuforums.org/showthread.php?t=1125400]("http://ubuntuforums.org/showthread.php?t=1125400")

---

### Post by AdrianVeidt on 2010-02-24
There is no nvidia-settings-190 package. Nvidia-settings in the PPA is called "nvidia-settings". Just run sudo apt-get update and sudo apt-get install nvidia-glx-190 nvidia-settings if you don't already have them and you'll be fine.

---

