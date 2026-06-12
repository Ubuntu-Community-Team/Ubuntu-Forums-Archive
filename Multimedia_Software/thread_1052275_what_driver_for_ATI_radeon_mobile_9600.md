---
title: "what driver for ATI radeon mobile 9600?"
date: 2009-01-27
forum: Multimedia Software
---

### Post by merlin666 on 2009-01-27
In 8.04 I used the fglrx package for my Mobility Radeon 9600 and it worked quite nice for compiz and google earth, though required a bit of work to get them to co-exist. After upgrading to 8.10 I lost gnome/xserver and had to do a clean-install (after 3 years of updating). Now, there is no graphic driver listed in the hardware menu, there is no entry for ATI in the Ubuntu Guide, and the ATI driver page only provides instruction up to 8.04. Where can I find instructions for graphic driver for my card so I have 3D rendering in Google Earth without having to disable compiz?

---

### Post by bettlebrox on 2009-01-27
There's a tool that should install the ATI driver for you. If your running Gnome, click on System->Administration->Hardware Drivers. It should automatically detect the ATI video card and ask if you want to "activate" the ATI driver. If that doesn't work, ask it shouldn't be too hard to get the driver installed from the command-line.

Luck! :)
Mick

---

### Post by merlin666 on 2009-01-29
That is the problem: there is no graphics driver listed in hardware, as was in 7.04, 7.10, and 8.04. That's why I looked to ubuntuguide, the ATI driver installation page and this forum to find guidance on manual instruction of either the open source radeon driver or the fglrx driver. But all the instructions only go up to 8.04, I have not been able to find much information for 8.10. 

It is very strange to have a blank xorg.conf for sure. Strangely enough, compiz and non graphical apps seem to work fine. Oh I should add:

$ sudo glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: DRI R300 Project

Is this 3d-accelerated or not, or should I try to install the Mesa or fglrx driver?

---

### Post by bettlebrox on 2009-01-29
I was surprised too when I 1st looked at xorg.conf when I upgraded to Intrepid. Intrepid uses a new improved version of Xorg that (for most hardware) auto-detects the settings. That's why your xorg.conf looks so bare! :)

What happens when you try what I suggested?
[INDENT]Click on System->Administration->Hardware Drivers[/INDENT]

---

### Post by merlin666 on 2009-01-29
> **bettlebrox said:**
> I was surprised too when I 1st looked at xorg.conf when I upgraded to Intrepid. Intrepid uses a new improved version of Xorg that (for most hardware) auto-detects the settings. That's why your xorg.conf looks so bare! :)

What happens when you try what I suggested?
[INDENT]Click on System->Administration->Hardware Drivers[/INDENT]
Thanks, the only hardware driver listed is the one for the wireless (which actually works, though without WAP).

---

### Post by bettlebrox on 2009-01-30
Try installing the xorg-driver-fglrx package and see what happens.

What make/model laptop is this? Does it have switchable graphics (dual GPU's)? Did you changes any settings in the BIOS?

---

### Post by darinmiller@cableone.net on 2009-02-07
I have the same issue.  Up until 8.04, I could enable my ATI Radeon 9600 mobile in the hardware settings, then install the latest ATI drivers. 

However, installing the ATI drivers fails to activate the video card. ATI control center says to reinstall the driver or run ati-config - neither works.

---

### Post by CarpKing on 2009-02-10
You might have to specify fglrx in xorg.conf if it isn't autodetecting it.  Also, newer versions of fglrx have been reported to not work for some people with r300-based cards (like the 9600), and I don't know if the latest version fixes that or not.

---

