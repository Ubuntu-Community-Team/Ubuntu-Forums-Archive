---
title: "4 monitors and fglrx video drivers"
date: 2014-05-08
forum: Multimedia Software
---

### Post by alex199 on 2014-05-08
Short story, get **Error! Bad return status for module build on kernel: 3.13.0-24-generic (x86_64)** and **kernel includes at /lib/modules/3.13.0-24-generic/build/include not found or incomplete** when trying to install fglrx from amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64 for **two** Radeon HD 2600 XT. 

  Long story: when installing Ubuntu 14.04 from livecd monitor4 didn't get any signal and i got **Could not switch the monitor configuration/could not set the configuration for CRTC 64**  error. I pushed through. After the install and reboot monitor4 started  to work but 3 doesn't and got the same CRTC 64 pop up error at login  screen, also graphics/cursor is kinda jumpy and not smooth.
  Figured i'll to install fglrx drivers manually
```
$ sudo lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV630 XT [Radeon HD 2600 XT] [1002:9588]
04:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV630 XT [Radeon HD 2600 XT] [1002:9588]
```

```

$ sudo xrandr
Screen 0: minimum 320 x 200, current 7680 x 1200, maximum 8192 x 8192
DVI-0 connected primary 1920x1200+0+0 (normal left inverted right x axis y axis) 519mm x 324mm
   1920x1200      60.0*+
   1600x1200      60.0  
...more resolutions...
DIN disconnected (normal left inverted right x axis y axis)
DVI-1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 531mm x 299mm
   1920x1080      60.0*+   50.0     59.9  
   1920x1080i     60.1     50.0     60.0  
...more resolutions...
DVI-1-2 connected 1920x1080+3840+0 527mm x 296mm
   1920x1080      60.0*+   50.0     59.9     30.0     30.0  
   1920x1080i     60.1     50.0     60.0  
...more resolutions...
DIN-1-1 disconnected
DVI-1-3 connected 1920x1080+5760+0 527mm x 296mm
   1920x1080      60.0*+   50.0     59.9     30.0     30.0  
   1920x1080i     60.1     50.0     60.0  
...more resolutions...
  1920x1080 (0x45)  148.5MHz
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   67.5KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   60.0Hz
...more resolutions...

```


```

$ sudo dpkg -i fglrx*.deb
Selecting previously unselected package fglrx.
(Reading database ... 167116 files and directories currently installed.)
Preparing to unpack fglrx_8.970-0ubuntu1_amd64.deb ...
Unpacking fglrx (2:8.970-0ubuntu1) ...
Selecting previously unselected package fglrx-amdcccle.
Preparing to unpack fglrx-amdcccle_8.970-0ubuntu1_amd64.deb ...
Unpacking fglrx-amdcccle (2:8.970-0ubuntu1) ...
Selecting previously unselected package fglrx-dev.
Preparing to unpack fglrx-dev_8.970-0ubuntu1_amd64.deb ...
Unpacking fglrx-dev (2:8.970-0ubuntu1) ...
Setting up fglrx (2:8.970-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
** update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist**
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.970 DKMS files...
First Installation: checking all kernels...
Building only for 3.13.0-24-generic
Building for architecture x86_64
Building initial module for 3.13.0-24-generic
[B]Error! Bad return status for module build on kernel: 3.13.0-24-generic (x86_64)
Consult /var/lib/dkms/fglrx/8.970/build/make.log for more information.[/B]
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Setting up fglrx-amdcccle (2:8.970-0ubuntu1) ...
Setting up fglrx-dev (2:8.970-0ubuntu1) ...
Processing triggers for initramfs-tools (0.103ubuntu4) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-24-generic
Processing triggers for libc-bin (2.19-0ubuntu6) ...

```


```

$ cat /var/lib/dkms/fglrx/8.970/build/make.log
DKMS make.log for fglrx-8.970 for kernel 3.13.0-24-generic (x86_64)
Wed May  7 21:44:57 EDT 2014
AMD kernel module generator version 2.1
kernel includes at /lib/modules/3.13.0-24-generic/build/include not found or incomplete
file: /lib/modules/3.13.0-24-generic/build/include/linux/version.h


```


```

$ sudo dpkg -l | grep linux-headers
ii  linux-headers-3.13.0-24                               3.13.0-24.47                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                       3.13.0-24.47                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.24.29                                        amd64        Generic Linux kernel headers
```

so the headers are installed but that file **/lib/modules/3.13.0-24-generic/build/include/linux/version.h** is infact missing


```
$  uname -r
3.13.0-24-generic

```

```

$ X -version

X.Org X Server 1.15.1
Release Date: 2014-04-13
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu


```

---

### Post by alex199 on 2014-05-09
To answer my own question amd dropped support for my card and left it with legacy drivers which cannot be installed on 14.04 due to X version

---

