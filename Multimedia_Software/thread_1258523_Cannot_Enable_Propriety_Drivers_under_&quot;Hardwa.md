---
title: "Cannot Enable Propriety Drivers under &quot;Hardware Drivers&quot;"
date: 2009-09-05
forum: Multimedia Software
---

### Post by Loafers on 2009-09-05
I've been trying to install the driver for my ATI X300 by following the guide [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20from%20Ubuntu%20repositories%20(easier)](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20from%20Ubuntu%20repositories%20(easier))

However, it says,
> Enable the accelerated ATI graphics driver in the 'Hardware Drivers' (System->Hardware drivers), then do: 

Which, there is nothing listed on mine to enable...  I've tried the "Install from ati.com (latest version of drivers)" method, but I ended messing up xorg configuration and had to reinstall Ubuntu.  My last resort.

Before Jaunty, when I installed Intrepid out of the box and ran the Update Manger, it would never fail to give me the option of enabling my Proprietary hardware drivers, but since Jaunty, it does not ask nor even SHOW that any proprietary hardware drivers available...  I have all software sources enabled, so that shouldn't be the problem... Why is this?!

Any suggestions?

---

### Post by hal10000 on 2009-09-05
First find out if you have the ATI driver loaded:
Try [COLOR="Red"]lsmod | grep fglrx[/COLOR]
If you get no answer, then try to load it manually: [COLOR="Red"]sudo modprobe fglrx[/COLOR]
just to verify wether you have the correct driver. if you don't have it, then maybe you have to install the package **xorg-driver-fglrx** and then reenable them in System--->Hardware drivers.

I dont have an ATI card, so I'm not sure what else you could do.

---

### Post by Loafers on 2009-09-05
> **hal10000 said:**
> First find out if you have the ATI driver loaded:
Try [COLOR="Red"]lsmod | grep fglrx[/COLOR]
If you get no answer, then try to load it manually: [COLOR="Red"]sudo modprobe fglrx[/COLOR]
just to verify wether you have the correct driver. if you don't have it, then maybe you have to install the package **xorg-driver-fglrx** and then reenable them in System--->Hardware drivers.

I dont have an ATI card, so I'm not sure what else you could do.

At this very moment, I think I may have figured out the problem.  I did some more researching and dug this from the [ATI Wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Before_you_start")

> Which cards does ATI no longer support? The ATI Radeon 9500-9800, X300-X2100, Xpress. See the complete list here. If your card is on that list, you are restricted to the 9.3 driver - however since 9.3 driver doesn't support xorg-xserver 1.6, it will not work with Jaunty! This guide currently is for installing 9.7. !!!SO BE CAREFUL!!! 

I guess this would explain why Juanty doesn't allow me to enable?

Sigh... I guess I'll revert back to Intrepid or Window$...

---

