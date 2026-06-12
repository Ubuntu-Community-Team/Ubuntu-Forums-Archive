---
title: "[SOLVED] HDTV Resolution in mythbuntu"
date: 2008-12-03
forum: Multimedia Software
---

### Post by fowie on 2008-12-03
I had my mythtv box all ready to go but now that I've plugged it into my HDTV I don't see anything.  I'm using a liveCD of Mythbuntu 8.10 now to see if I can get it working.  Mythbuntu boots up but I don't get any display.  After re-starting gdm a few times I can get a wonderfully naive box telling me that ubuntu is now running in low-res mode (when it's actually running at 1600x1200).  If I try to re-detect the configuration it doesn't work, in fact, the only thing that does work is to just go ahead with "low res" mode and then in XFCE change the settings.  Great, except that the only resolutions in XFCE settings are ones I don't want.  It's a widescreen TV so I want 1324x768 or whatever that resolution is, but that's not an option.  Intrepid has gotten rid of any xorg.conf usable information....HELP!

Update:

After looking through my Xorg.0.log I've found plenty of information, but no solutions.  My graphics card is the intel 82865G Integrated Graphics Controller rev 2.  I can get to the 1600x1200 resolution mode if my Device section of xorg.conf has "vesa" as the driver.  If I try to switch to "i810" as the driver I get the error "no device found"
Xorg.0.log shows that the module i810 is loaded, and then 
```

(II) intel: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100, i810e, i815, i830M, 845G, ......865G.... Mobile Intel GM45 Express Chipset, .......
(II) Primary Device is: PCI 00@00:02:0
(EE) No devices detected.

```

any ideas?

---

