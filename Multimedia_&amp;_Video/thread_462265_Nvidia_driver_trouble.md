---
title: "Nvidia driver trouble"
date: 2007-06-02
forum: Multimedia &amp; Video
---

### Post by Curnel_D on 2007-06-02
I'm having trouble installing the drivers for my 7600 go.  Downloaded the latest version from the nvidia linux download page.  You'll see down at the bottom the error messages I'm getting in the nvidia installer.  Any help at all would be really appreciated.

Thanks. 




{code}
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat Jun  2 14:24:06 2007

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
WARNING: Skipping the runlevel check (the utility `runlevel` failed to run).
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID
   '16133' of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       [www.nvidia.com](www.nvidia.com).
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.{/code}

---

### Post by dfreer on 2007-06-02
To install the official driver from nvidia's website, you have to exit X in order to install it (the correct command I believe would be to do a sudo /etc/init.d/gdm stop and then a <Ctrl><Alt><Backspace>.

If you don't mind me saying, unless there is a specific reason you need to use the .run package from nvidia, you can install the newest driver REALLY quick without having to kill X server. Either use the Restricted Driver Manager in Feisty 7.04, or use this command:
```
sudo apt-get install nvidia-glx-new
```
And then edit your /etc/X11/xorg.conf file accordingly.

---

### Post by Curnel_D on 2007-06-02
Thanks.  Honestly, I'm extremely new to linux, and had almost no idea what I was doing.

---

### Post by dfreer on 2007-06-02
Well at least you found ubuntuforums, another place to check is ubuntuguide.org
Between these two sites, you should have no problems with ubuntu!! Good luck and welcome to ubuntu!

BTW, the easiest way is to use the Restricted Drivers Manager, it makes things SO simple.

---

### Post by tseliot on 2007-06-02
you can also use this guide:
[http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)

---

