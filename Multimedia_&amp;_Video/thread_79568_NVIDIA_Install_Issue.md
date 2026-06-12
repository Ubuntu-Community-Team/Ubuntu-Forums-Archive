---
title: "NVIDIA Install Issue"
date: 2005-10-20
forum: Multimedia &amp; Video
---

### Post by jpfinley on 2005-10-20
I have downloaded NVIDIA's driver and am able to sucessfully execute the .run file (thanks to the help in [this thread]("http://ubuntuforums.org/showthread.php?t=75345")).

The install process doesn't get very far until the installer throws down some errors.  They have to do with kernel interfaces, apparently.  My machine is a Dell Inspiron 9300 with a NVIDIA geForce Go 6800 card, running Ubuntu 5.10.  I have included /var/log.nvidia-installer.log.
```

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Oct 20 13:03:37 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
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
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

This forum has been a great resource for my Ubuntu install so far and I appreciate all the help that you guys do for new kids like me. Thanks!

---

### Post by Pausanias on 2005-10-23
There is a much simpler way to install the drivers. You don't need to download anything from NVIDIA. Just download the correct driver from the repositories.

```
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable

```

You will have to type in your password after the first line.  AFter the last line reboot and you should be OK.

---

