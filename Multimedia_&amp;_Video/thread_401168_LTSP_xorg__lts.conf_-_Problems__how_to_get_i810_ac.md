---
title: "LTSP xorg / lts.conf - Problems / how to get i810 accelerated?"
date: 2007-04-04
forum: Multimedia &amp; Video
---

### Post by geograf on 2007-04-04
I'm running a 700Mhz ThinClient with i815 Chipset with my Ubuntu Terminalserver

It works principally, but i get very strange effects by changes of the xorg-Parameters in ltsp.conf 

**Initial Situation:**
Without any X-Parameters in lts.conf, the terminal runs with 1280x1020, 24 Bit and 82Hz - the same  parameters as my CRT "MainScreen" at the server himself

**Target: **The terminal should run with:
- only 60 Hz, because there is a TFT-Display  connected
- only 16Bit Color, because there are instabilities with 24 Bit and the graphic acceleration in xorg i810 Driver only works with 16 Bit on i810-Chipset (see man i810)
- the (minimal) grapic acceleration the i810-Chipset provides (some simple OpenGL Games/Sreensavers and viewing DVDs should be posible)
[B]
The trouble:[/B]
setting  X_COLOR_DEPTH=16 in lts.conf works, but switches the terminal to 1600x1200 resolution (!?)
setting X_MODE_0  = 1280x1024 (or below) is effectless - nothing changes...
setting X_VIDEORAM = "32786" seems also effectless  - graphic acceleration doesn't work

[B]
Questions[/B]
* how can I set the 1280x1024, 16 Bit, 60Hz mode?
* how can I view the xorg.log? (where is it? i guess, there is a temp.RAMDISK in the Terminal) 
   - ***how can I login localy into the terminal*** (user? password?)
* is there a way to provide a seperate xorg.conf for the terminal? - OK, there are XF68Config-Parameters for lts.conf. - But Ubuntu uses X.Org, and the xorg.conf is in another path as XF86Config..

* the Master Question: **how can I get the i810 acceleration running?**

any help welcome...

---

