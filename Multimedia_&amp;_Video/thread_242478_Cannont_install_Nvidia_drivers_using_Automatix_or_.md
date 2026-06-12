---
title: "Cannont install Nvidia drivers using Automatix or EasyUbuntu"
date: 2006-08-23
forum: Multimedia &amp; Video
---

### Post by Clark Nova on 2006-08-23
I've decided to try using my Nvidia card instead of my ATI 9800 pro to see if I can get the hardware acceleration working. I cannot seem to get the drivers installed however, perhaps I still have the old drivers installed somehow (even though I never really got them installed correctly) and need to clean them out somehow.

When I try to run EasyUbuntu to install the drivers I am getting this error message:

/bin/sh: nvidia-glx-config: command not found

I assume that means that it is searching for a component that isn't installed correctly?

Can somebody help me out with this, it's perhaps the main thing that's stopping me from switching to Linux full-time :(


**edit**

I tried running the Nvidia driver installer from the Nvidia site. I ended my X session (it said it wouldn't install while it was running). I ran through the wizard but it failed and pointed me to /var/log/Nvidia-installer.log for details of why. Here are the contents of that file:

> nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Aug 24 00:27:34 2006

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
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
WARNING: Skipping the runlevel check (the utility `runlevel` failed to run).
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Performing CC test with CC="cc".
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' RPM installed.  If you
       know the correct kernel source files are installed, you may specify the
       kernel source path with the '--kernel-source-path' command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).



Does that help shed any light on the problem for anybody?

Thanks for looking :)

---

### Post by mlind on 2006-08-23
Uninstall stuff that official nvidia-installer did. probably running the .run file with --uninstall parameter.


a) If you're **not** running a vanilla kernel:
```

sudo aptitude install linux-restricted-modules-$(uname -r)
sudo aptitude install nvidia-glx

```

b) If you're running a vanilla kernel:
```

sudo aptitude install module-assistant
sudo m-a a-i nvidia-kernel-source
sudo aptitude install nvidia-glx

```


Then change **nv** to **nvidia** from /etc/X11/xorg.conf
Then restart kdm/gdm
```

sudo /etc/init.d/?dm restart

```

---

### Post by Clark Nova on 2006-08-24
Thanks for replying! :)

I tried to install the drivers as you said but I go this error:

> simon@simon-desktop:~$ sudo aptitude install linux-restricted-modules-$(uname -r)
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done      
No candidate version found for linux-restricted-modules-2.6.15-26-386
The following packages have been kept back:
  libdvdcss2 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
simon@simon-desktop:~$ sudo aptitude install nvidia-glx
Reading package lists... Done
Building dependency tree... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  libdvdcss2 
The following NEW packages will be installed:
  nvidia-glx 
0 packages upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/4059kB of archives. After unpacking 12.5MB will be used.
Writing extended state information... Done
(Reading database ... 98084 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1.0.8762+2.6.15.11-1_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1.0.8762+2.6.15.11-1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1.0.8762+2.6.15.11-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
simon@simon-desktop:~$ 


Any ideas?

Thanks again.

---

### Post by tseliot on 2006-08-24
Try this:
1) Download Envy and install it (follow the instructions on the website):
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

2) type "envy" to launch it and select to "uninstall the driver"

3) start envy again and select to "install" the driver.

---

### Post by mlind on 2006-08-24
> **Clark Nova said:**
> Thanks for replying! :)

Any ideas?

Thanks again.

You don't have **restricted** repository enabled.. That's why you can't find linux-restricted-modules-2.6.15-26-386 package.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

or
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

