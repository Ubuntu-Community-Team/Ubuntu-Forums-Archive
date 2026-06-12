---
title: "Loading nv_drv instead of nvidia_drv"
date: 2007-04-09
forum: Multimedia &amp; Video
---

### Post by Squishy on 2007-04-09
I have bought a new video card and wanted to install the nvidia-glx drivers for it work. Got a black screen when starting X, so I tried the [www.nvidia.com](www.nvidia.com) drivers, same problem.

After looking more carefully at the Xorg.0.log it seems to load the nv_drv.so instead of the nvidia_drv.so, which is specified in my xorg.conf under "Device"

```

(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 2.0.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 1.1

```

I went through most of the guides here, but all with the same result.

Any idea why it would load the nv_drv anyway instead of the nvidia_drv, which it should?

---

### Post by tseliot on 2007-04-09
type:
sudo nvidia-xconfig

and restart the Xserver.

if that doesn't work I will need to know the output of the following commands:
```
ls -l /etc/X11/xorg*
```
```
ls -l /$HOME/xorg*
```

---

### Post by Squishy on 2007-04-09
> **tseliot said:**
> type:
sudo nvidia-xconfig

and restart the Xserver.
Same problem.


> if that doesn't work I will need to know the output of the following commands:
```
ls -l /etc/X11/xorg*
```
```
ls -l /$HOME/xorg*
```

```

erik@zoidberg:~$ ls -l /etc/X11/xorg*
-rw-r--r-- 1 root root 3496 2007-04-09 20:23 /etc/X11/xorg.conf
-rw-r--r-- 1 root root 4075 2007-04-08 15:26 /etc/X11/xorg.conf.20070407165033
-rw-r--r-- 1 root root 4061 2007-04-07 18:05 /etc/X11/xorg.conf.20070407180517
-rw-r--r-- 1 root root 4202 2007-04-07 20:39 /etc/X11/xorg.conf.20070407203931
-rw-r--r-- 1 root root 4206 2007-04-08 10:55 /etc/X11/xorg.conf.20070408105507
-rw-r--r-- 1 root root 3539 2007-04-08 12:52 /etc/X11/xorg.conf.20070408125210
-rw-r--r-- 1 root root 4208 2007-04-08 14:30 /etc/X11/xorg.conf.20070408143011
-rw-r--r-- 1 root root 3381 2007-04-09 15:47 /etc/X11/xorg.conf.20070409154726
-rw-r--r-- 1 root root 4227 2007-04-07 19:13 /etc/X11/xorg.conf_backup
-rw-r--r-- 1 root root 3500 2007-04-09 17:44 /etc/X11/xorg.conf.backup
-rw-r--r-- 1 root root 3539 2007-04-08 12:50 /etc/X11/xorg.conf_old
-rw-r--r-- 1 root root 3381 2007-04-09 15:46 /etc/X11/xorg.conf_werkend
erik@zoidberg:~$ ls -l /$HOME/xorg*
ls: //home/erik/xorg*: No such file or directory

```

---

### Post by Squishy on 2007-04-09
I've added the Xorg.0.log and the xorg.conf I used in the tar.gz

Might be of help.

---

### Post by Squishy on 2007-04-10
Still have the same problem. :(

---

### Post by Squishy on 2007-04-13
> **Squishy said:**
> Still have the same problem. :(

Someone have any idea? Please.

---

### Post by Squishy on 2007-04-14
When I use nvidia-glx (1.0-9631) it loads the nvidia_drv.so fine.

> 
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver


But then it gives me the API mismatch

> 
Error: API mismatch: the NVIDIA kernel module has the version 1.0-9755, but
this X module has the version 1.0-9631.  Please make sure that the kernel
module and all NVIDIA driver components have the same version.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***


When I install nvidia-glx-new to match the kernel module with the xorg driver it loads nv_drv.so again and then I get the blank screen and lockup.

---

