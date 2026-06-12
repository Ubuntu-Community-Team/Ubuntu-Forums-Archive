---
title: "DRI and MesaGL-hardware with ATI Rage Pro (Mobility M3) under Ubuntu 6.06?"
date: 2006-06-12
forum: Multimedia &amp; Video
---

### Post by drink on 2006-06-12
Hi, I have an IBM Thinkpad A21p which has ATI Rage Mobility M3 (Rage Pro) graphics. I don't get DRI or of course hardware OpenGL. I tried using the latest driver snapshot from the DRI project but their module doesn't load. How can I get DRI working on this card?

If you are not sure of the answer, note that the official ATI driver (fglrx) only supports Radeon 8500 and up or something like that; certainly no Mach64/Rage support.

---

### Post by boomstik on 2006-08-19
I also have this problem. Dell Inspiron 5000e with Rage Mobility M3 card. Cannot get DRI to work - I've tried everything I could find, including installing the snapshots from dri.freedeskop.org, etc, but no matter what I do I just get Mesa and no direct rendering. Has anyone ever got DRI to work on a Rage/Mach64 card? I just don't know what to try next, and whether there is even a point in trying. ](*,) 

Note that from other reports I've read I can gather than DRI works in Xfree86, but not in X.org. I've considered reverting to Xfree86, but my goal is glx and compiz. If it's possible to get those two running under Xfree86, I might take that option too.....

Please help if you can.... Thanks!

---

### Post by CalcProgrammer1 on 2007-05-17
In xorg.conf change Default Depth from 24 to 16, I have a ThinkPad A21p as well and it works great (only 16 bit color depth but awesome 3d support for screensavers, games, etc...)

I'm using 7.04.
I know this may be a bit late, but it'll help those who are searching for answers :)


...As for Xgl/Beryl/Compiz...No!  Sorry, but it doesn't work, needs 64mb video RAM, the M3 has only 16 :(

---

