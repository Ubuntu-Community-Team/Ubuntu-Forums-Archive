---
title: "Getting 404 when installing Nvidia drivers"
date: 2006-09-17
forum: Multimedia &amp; Video
---

### Post by Trite on 2006-09-17
Okay, first let me say that I'm brand new to Ubuntu, and Linux altogether. So you must forgive me for being dumb. ;) 


Here's my problem. I'm having issues with the cursor lagging a little. I found this thread : [http://www.ubuntuforums.org/archive/index.php/t-65723.html](http://www.ubuntuforums.org/archive/index.php/t-65723.html) and have been going through all of the posts trying things.

Okay, right now I'm trying to install the Nvidia drivers. The wiki post lists these commands...

sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable


When I try the first one it fails. Here's the info

```
trite@crlocal:~$ sudo apt-get install nvidia-glx nvidia-kernel-common
Reading package lists... Done
Building dependency tree... Done
nvidia-kernel-common is already the newest version.
Suggested packages:
  nvidia-kernel-source
The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 4059kB of archives.
After unpacking 12.5MB of additional disk space will be used.
Err http://security.ubuntu.com dapper-security/restricted nvidia-glx 1.0.8762+2.6.15.11-3
  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/nvidia-glx_1.0.8762+2.6.15.11-3_i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```


Any idea where I'm screwing up?

Graphics card is an Nvidia GeForce 5200 Ultra.


Thanks guys. I'm sure there will be more stupid questions ahead from me. :)

---

