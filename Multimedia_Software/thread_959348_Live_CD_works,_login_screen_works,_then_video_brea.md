---
title: "Live CD works, login screen works, then video breaks (desperate!)"
date: 2008-10-26
forum: Multimedia Software
---

### Post by painaxl on 2008-10-26
Hey all,

I'm having a serious problem with an older computer I just put a fresh install of 8.10rc on.  First some background:

This computer ran Drake fine and was upgraded to Gutsy fine.  Earlier this year, I did a clean install of Heron to make a /home partition.  Everything worked for a while, but after what must have been an update (it's not my computer, so I don't know what update might have caused the issue), the following problem would happen: After logging in, the screen would switch resolutions once and I'd see the mouse.  Then, a flicker and the screen is all distorted with just one space of correctly displayed background with the cursor (which is no longer movable).  Then it distorts again and the system is completely frozen.  Under Heron, I was able to CTRL-ALT-BKSP and return to the login screen where I could select "failsafe GNOME", which would work.

I did a clean install of 8.10rc yesterday in hopes that with a fresh install, the problem would be eliminated.  The live CD displays the graphics perfectly and the installation went smoothly.  The login screen again displays fine.  However, when I log in, the same problems happen.  This time, though, "failsafe GNOME" does the same thing.  My only option upon logging in is getting to a terminal.

I've tried editing my Xorg.conf, but each field says automatically detected monitor/card etc.  I've also read from searching that newer versions of Ubuntu pretty much disregard xorg.conf anyways in favor of autodetecting.  Is that true?

The computer is an emachines with onboard graphics (intel chipset) and a CRT monitor that still works fine.  This is the first time I've been truly stuck with Ubuntu as I've been able to find my way around pretty much every other problem.

Any help or suggestions anyone would give would be HUGELY appreciated!

---

