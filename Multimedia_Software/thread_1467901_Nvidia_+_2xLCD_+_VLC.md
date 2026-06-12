---
title: "Nvidia + 2xLCD + VLC"
date: 2010-05-01
forum: Multimedia Software
---

### Post by EMCGFX on 2010-05-01
Computer Specs:
Core2Quad Q6600 @ 2.40GHz
4GB DDR2 Memory
250GB Hard Drive
XFX GeForce 9400GT 1GB DDR2 (VBIOS: 62.94.61.00.07) PCIE 16X
Nvidia Driver: 185.18.36
Dell 17" LCD (VGA) CRT-1
ViewSonic 20" LCD (DVI) DFP-0
Ubuntu 9.10 x64 Final (will also test this on 10.04 soon)
VLC 1.0.2

When I watch video in VLC and have compiz effects to default which is "Normal" under System > Preference > Appearance dialog. I have horizontal video lines when picture moves fast. By disabling the compiz effects, setting the Appearance to "None" this issue disappears. I just found this out, after countless tries and 2 days of headaches. This is what I figured out. The bug is in Compiz most likely. Because as soon as I disabled the effects it works good even in TwinView with two LCDs. The only down side is that I don't have any effects now. But as long as it works in TwinView I'm ok for now. If any one know how to patch this bug please let me know. Thank you.

EDIT: Tried same thing on 10.04 with TwinView + 2xLCDs + VLC. Its still has this horizontal lines cut bug with Nvidia driver 195.36.15. So this means that its something to do with Nvidia drivers after all. Too bad, I was hoping it would work at least as it did with 185.18.36 on Ubuntu 9.10.

EDIT2: Now only one LCD and without compiz works, so don't know what is up with all this updates.

---

### Post by EMCGFX on 2010-06-16
Alright with countless tries I finally got my VLC video play well without any horizontal lines on one LCD, haven't tried on 2xLCDs just yet. Will report how that goes, after I post this. Big thank you to **mc4man** @ Ubuntu Forum with his help, I fixed the problem. I will makr this tread as SOLVED because at least one LCD works with compiz properly now. Here is what I did.


NVidia Driver: 195.36.24


VLC Settings
-------------
Tools -> Preferences -> Video
Output: Default


gksudo nvidia-settings
-----------------------
X Server XVideo Settings
Enable, Sync to VBlack
---
OpenGL Settings
Enable, Sync to VBlack


Compiz Config
--------------
System -> Preferences -> CompizConfig Settings Manager -> General -> General Options
Under General Tab, check "Unredirect Fullscreen Windows".
Under Display Settings, check "Sync To VBlack" and
Select Texture Filter, Best

---

### Post by EMCGFX on 2010-06-16
Yep, as expected. two LCDs are working good. I just needed to do this following thing. Once you have second LCD connected and working, do this.

gksudo nvidia-settings
----------------------
In "X Server XVideo Settings" select under "Sync to this display device" and select the LCD you want to watch VLC video in. This works like a charm.

Thank you every one for your help, Ubuntu 10.04 LTS works for me good now.


NOTE: This issue still occurs with horizontal lines if you have your vlc window small, not in full screen. But I hardly use it this way, so its all good for me LOL Will try to find a fix for that now, will post on my findings.

---

### Post by dino99 on 2010-06-16
can you change the title: add howto

thanks

---

### Post by EMCGFX on 2010-06-17
> **dino99 said:**
> can you change the title: add howto

thanks

Done, mate.

---

