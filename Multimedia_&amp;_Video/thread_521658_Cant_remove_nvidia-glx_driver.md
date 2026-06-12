---
title: "Cant remove nvidia-glx driver"
date: 2007-08-09
forum: Multimedia &amp; Video
---

### Post by HgBoy on 2007-08-09
I used envy to install the nvidia-glx driver for my 7300gs. I have since found out that this is isnt the correct driver. When I try to use envy to remove this, it wont let me. When I try to install the nvidia-glx-new driver, I get this error message.

ustin@austin-desktop:~$ sudo apt-get install nvidia-glx-new
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  nvidia-settings nvidia-new-kernel-source
The following NEW packages will be installed:
  nvidia-glx-new
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4833kB of archives.
After unpacking 14.7MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  nvidia-glx-new
Install these packages without verification [y/N]? y
(Reading database ... 138828 files and directories currently installed.)
Unpacking nvidia-glx-new (from .../nvidia-glx-new_1.0.9755+2.6.20.5-16.29_i386.deb) ...
dpkg-divert: `diversion of /usr/X11R6/lib/libGL.so.1 to /usr/X11R6/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new' clashes with `diversion of /usr/X11R6/lib/libGL.so.1 to /usr/X11R6/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx-new_1.0.9755+2.6.20.5-16.29_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-new_1.0.9755+2.6.20.5-16.29_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I am running 2.6.20-16-generic kernel, ubunty 7.04

---

### Post by tbroderick on 2007-08-09
Why doesn't envy remove the old nvidia driver?

---

### Post by tseliot on 2007-08-10
@ tbroderick
Make sure you use Envy's latest release which does solve such problems.


@HgBoy
If you don't use Envy you might simply type:
```
sudo dpkg-divert --rename --remove /usr/X11R6/lib/libGL.so.1
```

then:
```
sudo apt-get install -f
```

```
sudo apt-get remove --purge nvidia-glx*
```
```

sudo apt-get install nvidia-glx-new
```

---

### Post by HgBoy on 2007-08-10
I purged envy, and installed the latest version, and have the proper drivers working now. Now if I could just get my resolution working properly. A small border around the screen is outside the actual viewing area, even though I have the resolution set properly. 

In more detail here... [http://ubuntuforums.org/showthread.php?t=521492]("http://ubuntuforums.org/showthread.php?t=521492")

---

