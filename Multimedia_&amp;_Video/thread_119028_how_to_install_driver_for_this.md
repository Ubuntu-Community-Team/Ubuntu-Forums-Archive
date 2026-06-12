---
title: "how to install driver for this?"
date: 2006-01-18
forum: Multimedia &amp; Video
---

### Post by crixtiano on 2006-01-18
His, please, my PC has the follow video card:

=======================================
$ lspci
(...)
0000:01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
=======================================



=======================================
$ lspci -n
(...)
0000:01:00.0 0300: 5333:8d04
=======================================


Where can I find a driver for this chipset and how to install a driver for this chipset?

10ks

Cristiano

---

### Post by MartinG on 2006-01-18
[QUOTE=crixtiano]His, please, my PC has the follow video card:

0000:01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

Where can I find a driver for this chipset and how to install a driver for this chipset?[/QUOTE]
It should have been detected and installed on setup.  I don't use this chipset, and yet on my machine I find I have loads of drivers as part of the base install, including:
xserver-xorg-driver-s3
xserver-xorg-driver-s3virge
xserver-xorg-driver-savage
One of these (probably the last) should be the one.

Are you saying you have no driver?
Have you tried re-configuring the x server?```
sudo dpkg-reconfigure xserver-xorg
```Are you getting an error message?  If so, what is it?

---

### Post by cvmostert on 2006-08-29
> **MartinG said:**
> It should have been detected and installed on setup.  I don't use this chipset, and yet on my machine I find I have loads of drivers as part of the base install, including:
xserver-xorg-driver-s3
xserver-xorg-driver-s3virge
xserver-xorg-driver-savage
One of these (probably the last) should be the one.

Are you saying you have no driver?
Have you tried re-configuring the x server?```
sudo dpkg-reconfigure xserver-xorg
```Are you getting an error message?  If so, what is it?

I also have this video card and have problems after upgrading to dapper... the screen blinks before i start to view any video and now the whole pc hangs when i want to play streaming videos from beelinetv.... 

I will try to reconfigure xserv... 
will keep you posted.
c

---

