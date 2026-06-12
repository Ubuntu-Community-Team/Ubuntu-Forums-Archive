---
title: "Failed to roll back driver from Nvidia beta 180.06"
date: 2008-11-17
forum: Multimedia Software
---

### Post by robertyou on 2008-11-17
Here is what I've done so far:

Installed nvidia linux beta driver 180.06, I deactivated the version 177.80 through "Hardware Drivers" first and stopped gdm from a console and so...

After finished some testing on the driver, again I stopped gdm and uninstalled the beta drier:
```
sudo sh NVIDIA*.run --uninstall
```

Everything until here was working without any problem. Now I can't activate nor install nvidia-glx-177 anymore.

From terminal:
```

bebo@beubu_gen:~$ sudo apt-get install nvidia-glx-177 nvidia-177-kernel-source
[sudo] password for bebo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-177-kernel-source is already the newest version.
nvidia-177-kernel-source set to manually installed.
The following NEW packages will be installed:
  nvidia-glx-177
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8931kB of archives.
After this operation, 25.8MB of additional disk space will be used.
(Reading database ... 125211 files and directories currently installed.)
Unpacking nvidia-glx-177 (from .../nvidia-glx-177_177.80-0ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/nvidia-glx-177_177.80-0ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libGL.so.1', which is also in package libgl1-mesa-glx
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-177_177.80-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
bebo@beubu_gen:~$ 

```

From synaptic package manager:
**Screenshots see attachment

As from Hardware Drivers, it displayed a message saying a program crashes during installation. It only showed up once, sorry I don't have any screenshot.

Much appreciated if someone can provide any idea or clue for me to fix it.:)

---

### Post by robertyou on 2008-11-19
Update..

Seems to me that the installer of nvidia beta driver had removed some vital files in the library during the un-installation, resulting some broken links related to nvidia-glx-177 package.

I've tried to re-install some packages that showed up on terminal error message to see if that'll fix the broken links. Nevertheless, came across this bug report which pretty much describes my problem..

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/287470](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/287470)

---

### Post by kpkeerthi on 2008-11-19
> 
dpkg: error processing /var/cache/apt/archives/nvidia-glx-177_177.80-0ubuntu2_i386.deb (--unpack):
**[COLOR="Red"] trying to overwrite `/usr/lib/libGL.so.1', which is also in package libgl1-mesa-glx[/COLOR]**
Processing triggers for man-db ...


Try removing libgl1-mesa-glx using apt-get.

---

### Post by robertyou on 2008-11-19
would really like to try that but then a bunch of packages will have to remove with it..

---

