---
title: "Fix compiz memory leak using Nvidia beta driver"
date: 2008-05-19
forum: Multimedia Software
---

### Post by nanog on 2008-05-19
A new nvidia box was driving me crazy. Over time compiz was accumulating ram to the point of taking up 7 gigs on an 8 gig box. Apparently this only occurs with certain nvidia cards with less than 256 mb of memory.

**Installing the Nvidia 173.08 beta driver made this box usable again!**
Disclaimer: **[COLOR="Red"]Its a beta so use at your own risk.[/COLOR]**

[COLOR="Blue"]**[https://bugs.launchpad.net/ubuntu/+source/compiz-fusion-plugins-main/+bug/151168](https://bugs.launchpad.net/ubuntu/+source/compiz-fusion-plugins-main/+bug/151168)**[/COLOR]
(Based on klerfayt's post in bug report.)



Nvidia drivers link
[COLOR="Blue"]**[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)**[/COLOR]

**Select appropriate driver using pulldown menu and click on driver link and download the installer script.**
As of 5-19 the driver was: Linux Display Driver Version 173.08 BETA.
In my case this was: NVIDIA-Linux-x86_64-173.08-pkg2.run.

[B]Download and make note of the location.
[/B]

**Open a terminal and issue the following commands:**

```
sudo apt-get remove --purge nvidia-glx-new nvidia-kernel-common
```
# if you have old driver then replace with nvidia-glx
# should remove restricted module ... if not remove manually

```
sudo apt-get install build-essential libc6-dev pkg-config xserver-xorg-dev
```

**Enter a TTY terminal **
[COLOR="Red"]**Ctl Alt F1 	**[/COLOR]		
This is necessary because we need to kill gnome.

```
sudo /etc/init.d/gdm stop
``` 	
# for kubuntu: sudo /etc/init.d/kdm stop

**Move to directory where driver is located and issue:**

```
sudo sh [NVIDIAdriverfile] 
```
In my case the command was:
sudo sh NVIDIA-Linux-x86_64-173.08-pkg2.run

You will have to compile a kernel module.

**I recommend that you allow nvidia to configure xorg.**

```
sudo reboot
```

---

