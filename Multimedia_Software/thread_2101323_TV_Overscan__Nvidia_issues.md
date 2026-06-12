---
title: "TV Overscan / Nvidia issues"
date: 2013-01-04
forum: Multimedia Software
---

### Post by MrRobogoat on 2013-01-04
Here are the specs behind the problem:
Philips 32PFL3403d TV  
Hooked up to a computer via a DVI -> HDMI adapter cable.

Computer:
EVGA Nvidia 9400 GT 
Kubuntu 12.10 i86_64 (running on an AMD Athlon X2 if that makes a difference)
Philips TV as the solo display (attempting a HTPC setup)

The problem I'm having is a overscan issue. It happens on Windows 7 when I first booted it up, but I fixed it by changing the resolution and scaling in the Nvidia driver. Since then, Windows has worked perfectly. I did get a *different* Kubuntu machine to work with this same TV, a Dell 4400M laptop with Nvidia 770M chipset. I had to use the command line, and it would only work while I had dual displays with one X-screen stretched across them. As soon as I closed the laptop lid the TV would go black. Not optimal for a HTPC, hence the switching around. 

I've tried messing with the same nvidia-settings command (#nvidia-settings -a CurrentMetaMode=" DFP-0: 1680x1050+0+0, DFP-1: 1920x1080+1680+0 {ViewPortOut=1820x1022+50+29}") but it causes the graphics to get really messed up. When I drag a window it leaves a trail of itself based on the refresh rate (if that makes any sense).

Based on some searching, I've poked at the EDID using get-edid and parse-edid. The one I got from Phoenix in Windows came back as being corrupt, perhaps a format issue? The parsing I received from #sudo get-edid | parse-edid said that the first bytes don't match EDID version 1 header, do not trust output(if any). The resolutions do not make any sense either, it's almost as if they are flipped (9:16 instead of 16:9).

Thoughts?

---

