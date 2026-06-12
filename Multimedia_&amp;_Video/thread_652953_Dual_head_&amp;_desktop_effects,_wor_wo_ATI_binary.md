---
title: "Dual head &amp; desktop effects, w/or w/o ATI binary driver won't cooperate"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by xVariable on 2007-12-29
Let me preface this post by saying that 7.10 is the most impressive Linux effort yet in my eyes. I'm one of those people that you see posting on forums saying, "This happens every time. There are several show-stopper issues with this release. You've had forever to get this right and still can't seem to manage it. This is the LAST time I'm trying Linux. I give up it will never be ready".  7.10 is the first distro I've tried that has floored me: 8 second boot times, more or less feature-complete, and most things work... except for this dual-display issue.  I'm writing an article comprising both a review of this version and an install guide. Hopefully you can help get this working. ;)

I'll give you my display setup.  If you need any more info let me know. My video card is an ATI x850 XT Platinum Edition (256 MB) with 1 DVI, 1 VGA, and 1 TV-out. There is a Dell 2407WFP 24" (1920x1200) connected to the DVI, and a Dell 20" 2001fp (1600x1200) connected to the VGA. There is nothing connected to the TV-out.

When I boot off the CD both displays are driven at 1600x1200.  I'm assuming this is so that the 20" doesn't get over-driven? Or is it because the VGA-out is presumed to be the default port? Anyway, install goes great. I boot to the desktop, and have the same arrangement with the displays as above. I'm also able to enable "Extra" visual effects in the Appearance applet and am able to enable true transparency in the terminal.

If I bring-up the Screens and Graphics applet, the secondary display is disabled, and I can't enable it. I can only set it as "Default screen".  If I enable it, and press "Detect", it gets detected as the 24" Dell connected to the DVI port.  Additionally, the primary display - the 24" - can't be set to anything higher than 1600x1200, even though it supports 1920x1200. So, it seems the system is getting confused as to what display is on what port, and what each display is capable of?  Finally, I can't set the secondary display as the Default screen. The settings don't save.

So, I tried the Restricted driver. I restarted the computer and the 24" displays 1920x1200, as does the 20" (the latter in "panning mode"). The problem is that now the desktop effects have been disabled and can't be enabled.  I go into the Screens and Graphics applet and can now enable the secodary display. I set it as a Dell 2001fp (analog), leave the res at the default of 640x480 in an attempt not to complicate things, click OK, and restart. The system restarts, the secondary display turns off, and the primary's output is corrupted, displaying thin vertical orange lines. I'm assuming it's trying to display the 640x480 output that the secondary display was set to?

So what do I do? Ideally I'd like to have the Restricted driver, driving both displays at their native res, with desktop effects enabled.

---

### Post by xVariable on 2007-12-30
*bump*

Anyone? I'd really like to get some semblance of this working. Something else I've noticed is that, with the restricted driver enabled, the card's fan runs at full speed 24/7, and it sounds like a jet engine.

---

