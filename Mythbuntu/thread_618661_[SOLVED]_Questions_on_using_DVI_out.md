---
title: "[SOLVED] Questions on using DVI out"
date: 2007-11-20
forum: Mythbuntu
---

### Post by ubnewbie2 on 2007-11-20
If I use DVI out, it will be via a DV_-HDMI cable to my flat panel TV. The TV says it only accepts certain standard resolutions via HDMI (720p, 1080i)

So does this mean that I will not be able to see anything on the screen until it has fully booted into X windows.  I understand tha xorg.conf controls the X windows resolution etc, but what, if anything, determines the screen res while the bios, grub, and mythbuntu boots?

Also, in Mythbuntu, I am running the proprietary drivers for my nvidia 7200 card. The gui lets me choose composite/svideo/component, but not DVI.   Can the gui turn on the DVI? or will it be on by default?

Also, I don't see 720p or 1080i as options for screen res in the mythbuntu gui.

or must I ignore the gui and just edit xorg.conf manually

---

### Post by superm1 on 2007-11-20
DVI/HDMI resolutions are detected by the EDID your tv puts out.  You don't configure them as "tv out types".  They are more so monitor resolutions.   Your TV should be able to handle the BIOS resolutions too (640x480 usually) even if it doesn't advertise it.

---

### Post by ubnewbie2 on 2007-11-20
> **superm1 said:**
> DVI/HDMI resolutions are detected by the EDID your tv puts out.  You don't configure them as "tv out types".  They are more so monitor resolutions.   Your TV should be able to handle the BIOS resolutions too (640x480 usually) even if it doesn't advertise it.

That's good news then. I will plug it in and see what happens (it's anew machine that is just running with a computer LCD panel on the bench at the moment)

Thanks.

---

### Post by ubnewbie2 on 2007-11-21
Works fine, as far as, the screen displays all resolutions I have thrown at it.  I just need to sort out which res I will use, and solve an overscan problem.

Thanks

---

### Post by champracer29 on 2008-01-06
Hi,

I am not able to display 1080 on my LCD TV using DVI - HDMI cable.

I just build HTPC case with Nvidia 8500 gt and 500 gb harddrive. I am able to display but show real poor video, even while i tried to set it as widescreen doesn't show good. I haven't adjust any settings execpt resoultion.

Any advise please? Thanks!

---

