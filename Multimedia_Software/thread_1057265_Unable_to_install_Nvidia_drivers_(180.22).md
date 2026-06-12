---
title: "Unable to install Nvidia drivers (180.22)"
date: 2009-02-01
forum: Multimedia Software
---

### Post by CRIMPS on 2009-02-01
I have been trying to install the newest Nvidia drivers from their website.  After some kernel updates three weeks ago, I lost all functionality of 3d graphics.  So, I have been impatiently waiting for a fix.  I found out that there was a new driver update available so I thought I would give it a try.  My problem is that I have been unable to install the driver.  In all the steps I have tried I can't even run in 2d mode, so I am stuck in low graphics mode.

So, I think I want to try one more time to install this driver.  If this doesn't work, I will be forced to reformat.  By the way, I haven't been able to successfully enable any of the other drivers from synaptic because I receive errors after rebooting and trying to start X.

Im running Ubuntu 8.10, Nvidia GeForce 8800GT.  I have all compiz and Nvidia components uninstalled and completely removed via Synaptic.

Here is the error from the Nvidia-Installer Log file I receive when trying to install:

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Feb  1 14:54:04 2009
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
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
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
-> Installing NVIDIA driver version 180.22.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> The CC version check failed:
   
   The compiler used to compile the kernel (gcc 4.2) does not exactly match the
   current compiler (gcc 4.3).  The Linux 2.6 kernel module loader rejects kern
   el modules built with a version of gcc that does not exactly match that of t
   he compiler used to build the running kernel.
   
   If you know what you are doing and want to ignore the gcc version check, sel
   ect "No" to continue installation.  Otherwise, select "Yes" to abort install
   ation, set the CC environment variable to the name of the compiler used to c
   ompile your kernel, and restart installation.  Abort now? (Answer: No)
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
       installed.  If you know the correct kernel source files are installed,
       you may specify the kernel source path with the '--kernel-source-path'
       command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

I did try installing gcc 4.2.  But I feel like I am missing a step with this.

---

### Post by alkamid on 2009-02-18
Try getting headers for your kernel
```
sudo apt-get install linux-headers
```

---

