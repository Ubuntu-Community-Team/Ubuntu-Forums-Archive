---
title: "nvidia-glx install failure... removal hell?"
date: 2009-03-10
forum: Multimedia Software
---

### Post by srilyk on 2009-03-10
So, gone are the days of dependency hell, but I may have run across a removal hell.

```
wayne@media-box:~$ sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  nvidia-kernel-source nvidia-settings
The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3854kB of archives.
After this operation, 12.3MB of additional disk space will be used.
(Reading database ... 367599 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1%3a96.43.05+2.6.24.16-24.57_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1%3a96.43.05+2.6.24.16-24.57_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1%3a96.43.05+2.6.24.16-24.57_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Someone had success by reinstalling xorg-driver-fglrx and removing it. Here's what I get when I try:

```
wayne@media-box:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/9952kB of archives.
After this operation, 30.1MB of additional disk space will be used.
(Reading database ... 367599 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_1%3a7.1.0-8-3+2.6.24.16-24.57_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx' clashes with `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/nvidia/libGL.so.1.2.xlibmesa by nvidia-glx'
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_1%3a7.1.0-8-3+2.6.24.16-24.57_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_1%3a7.1.0-8-3+2.6.24.16-24.57_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So then I find that there's this divert command:

```
wayne@media-box:~$ sudo dpkg-divert --rename --remove /usr/lib/libGL.so.1.2
Removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/nvidia/libGL.so.1.2.xlibmesa by nvidia-glx'
dpkg-divert: rename involves overwriting `/usr/lib/libGL.so.1.2' with
  different file `/usr/lib/nvidia/libGL.so.1.2.xlibmesa', not allowed

```

So... any idea what I'm missing?

Thanks for any help!

---

### Post by mikerobinson on 2009-10-23
I'm having the same issue

---

### Post by linux-hack on 2009-10-23
try doing a 
```
sudo apt-get install build-essential
```
and after install it

---

### Post by mikerobinson on 2009-10-23
> **boogy9 said:**
> try doing a 
```
sudo apt-get install build-essential
```
and after install it

It's already there:
> build-essential is already the newest version.

---

### Post by mikerobinson on 2009-10-23
Ok, I don't know how, but I figured out my problem. All I had to do was delete /usr/lib/nvidia/libGL.so.1.2.xlibmesa and then I could remove the diversion:

(I did this first)
> sudo aptitude purge nvidia-glx-new

then:
> sudo rm -r /usr/lib/nvidia
sudo sudo dpkg-divert  --remove /usr/lib/libGL.so.1.2
sudo aptitude purge xorg-driver-fglrx

---

