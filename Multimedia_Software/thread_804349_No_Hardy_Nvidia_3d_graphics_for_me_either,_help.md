---
title: "No Hardy Nvidia 3d graphics for me either, help?"
date: 2008-05-23
forum: Multimedia Software
---

### Post by dfro on 2008-05-23
I also have not been able to get 3d graphics working either. I have tried envyng.  When I enabled the nvidia driver that envy installed, I got the black screen. So, in recovery mode I did the xfix step to get my screen working again.

Now, I am trying the steps here:

[http://ubuntuforums.org/showthread.php?t=797270&highlight=Hardy+NVIDIA+drivers](http://ubuntuforums.org/showthread.php?t=797270&highlight=Hardy+NVIDIA+drivers)

.. and the downloaded NVIDIA 173.08 driver is giving me this error:

~$ cat /var/log/nvidia-installer.log
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri May 23 02:00:24 2008

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
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
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
       driver download page at [www.nvidia.com](www.nvidia.com).

_________________________________________

Any ideas on what to do next?

Thanks,
 dfro

p.s Are there any video card companies that are open-sourcing all of their driver code so that I can buy their video cards and get rid of the nvidia card?

---

### Post by dfro on 2008-05-23
After doing some reading on Linux and graphics drivers and the development cycle for drivers, I understand the problems with Nvidia and 3d graphics. An OS update most often requires a video card driver update to follow it. The problem is that Nvidia may update its black box to work with the latest distro of ubuntu sooner, maybe later, maybe much later (like never, if it is an old card).  This is no way for me to maintain productivity on my linux box. So goodbye Nvidia.

I want to support AMD-ATI for embracing open-source 2D/3D drivers on their cards.  So I am going to get rid of my NVIDIA card and get an ATI card. 

Does anybody have any suggestions for ATI cards that are running blender and k3d in ubuntu hardy?

Thanks,

dfro

---

