---
title: "What is correct 10.10 driver fornVidia Corp. NV18?"
date: 2010-10-24
forum: Multimedia Software
---

### Post by cigtoxdoc on 2010-10-24
What is correct driver for 10.10 for a nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3) (prog-if 00 [VGA controller]).

Originally, xorg driver 1.9 would work, now it won't.  

John

---

### Post by cigtoxdoc on 2010-10-29
I have a work-around, but I do not know why it works.  I tried several different approaches posted on this forum.  For some unknown reason, I found something that works.  I am running 1280 x 960 at 85 Hz.  I had to change my monitor to one on the shelf (Compaq 7550) that would run at 85 Hz.

The xorg configuration file is attached.  Segments from Hardware info are shown below:

-Display-
Resolution		: 1280x960 pixels
Vendor		: The X.Org Foundation
Version		: 1.9.0
-Monitors-
Monitor 0		: 1280x960 pixels

VGA compatible controller		: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3) (prog-if 00 [VGA controller])

Under the Device section in the xorg-conf file, I had to change nvidia to nv to get Ubuntu to load in graphics mode.

John

---

### Post by sonnettie on 2010-11-03
This is not a fix, ive only been using Linux for a couple of days and even i can figure out all you have told this guy to do is disable the nvidia driver and reactivate the Linux default driver with no 3d support

obviously this is not what the guy wanted as he was already using this driver before he decided to go with the nvidia drivers. I know you were just trying to help but posts like this can cause problems especially for noobs like this guy is. 

a better fix would be to install an older version of the driver that works with this version of x or drop back to a previous version of x if it was stable and caused no problems as an older x version with working nvidia drivers must be better than a new x version with no 3d support??  

as im am a noob myself, to linux anyway, not pc's in general, maybe some one can confirm this and elaborate whether dropping back an x version or nvidia driver version (if possible) is better.

---

### Post by sonnettie on 2010-11-03
Here is the **new drivers** working for geforce4 mx etc on **Ubuntu 10.10 **

[ftp://download.nvidia.com/XFree86/Linux-x86/96.43.19/](ftp://download.nvidia.com/XFree86/Linux-x86/96.43.19/)   <<<x86 (ie pentium amd-xp etc)

[ftp://download.nvidia.com/XFree86/Linux-x86_64/96.43.19/](ftp://download.nvidia.com/XFree86/Linux-x86_64/96.43.19/)   <<64bit (amd64 etc)

---

### Post by cigtoxdoc on 2011-01-28
The new drivers for nVidia are now on Synaptic.  Install drivers reboot and follow instructions.

John

---

