---
title: "Intel GMA X3100 video drivers"
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by Syke on 2007-06-12
I see Gutsy has the latest Intel 2.0 drivers. Are the Feisty repositories going to get the latest Intel video drivers that'll support the X3100?

---

### Post by toaste on 2007-06-18
First, have you already enabled extra repositories (unsupported, backports, etc) and installed the "xserver-xorg-video-intel" package?  This is enough to get Beryl working on the 965 chipset's X3000 cards, so installing this package ought to do you some good.  I personally noticed that this build supports widescreen resolutions but doesn't seem to support use of the pixel shaders, so turn the blur filter off if using Beryl/Compiz/CompComm.

As for getting the very latest builds of the Intel driver, it probably won't happen for feisty because they depend on functionality not just in Xorg 7.2, but xserver 1.3 (note that in the feisty repos, the latest xserver-xorg-core is "1.2.0-3ubuntu8").

---

### Post by Syke on 2007-06-18
Thanks for the info. I'll submit a bug for the -intel drivers, maybe it'll get fixed that way. I've got the Feisty -intel driver loaded. 2D is fine, as is simple 3D like glxgears. If I turn on Feisty's desktop effects, it'll work for a few seconds. I can usually open a couple windows or menus, but it quickly freezes the whole machine.

---

### Post by cnshzj007 on 2007-06-22
The case Syke said above is the ugly things that I met many times.
where is the key of that case?

---

### Post by lahook on 2007-06-22
> **Syke said:**
> Thanks for the info. I'll submit a bug for the -intel drivers, maybe it'll get fixed that way. I've got the Feisty -intel driver loaded. 2D is fine, as is simple 3D like glxgears. If I turn on Feisty's desktop effects, it'll work for a few seconds. I can usually open a couple windows or menus, but it quickly freezes the whole machine.


I have the intel 82G965 and 2D and 3D work great. I can't get the correct resolution for the monitor. If I play Open Arena It plays fine, but if I turn on Desktop effects the computer will freeze when I exit the game. Without Desktop effects the computer will not freeze. I've been thinking of upgrading to Gutsy Gibbon to try out the 2.0 Intel drivers to see if it corrects my resolution problem. Which driver are you using "i810" or "intel"? In my "/etc/X11/xorg.conf" file shows I'm using "i810", should I change it to say"intel"?

---

### Post by Voland666 on 2007-07-07
Get the latest X3100 driver released by Intel here:

[http://ubuntuforums.org/showthread.php?t=494943](http://ubuntuforums.org/showthread.php?t=494943)

Hope this helps

---

