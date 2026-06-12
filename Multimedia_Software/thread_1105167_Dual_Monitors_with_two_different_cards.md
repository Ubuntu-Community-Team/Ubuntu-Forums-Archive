---
title: "Dual Monitors with two different cards"
date: 2009-03-24
forum: Multimedia Software
---

### Post by itendsnow on 2009-03-24
Okay, I've tried this many ways but I can't seem to find a specific thread that helps with this perticular problem:

I have two graphics cards:
An Onboard: Intel 82195G/GV/910GL
PCI (Not express): ATI Radeon 9250

The onboard Intel goes out to a 15" monitor (60hz refresh) 1024*768, which is situated to the left of my main monitor,
my main monitor is 17" (70hz refresh) at 1280*1024, which is connected to my second graphics card which is the ATI Radeon 9250.

Now at the moment I'm running Ubuntu 9.04 Alpha 4, and the graphics performance with the ATI card has improved alot however during install nothing seems to get written to xorg.conf, it just seems to be a very empty file.

My BIO's is set to use the ATI card as the main card, and if I set it to use the Intel one Ubuntu adapts however I can't seem to get Ubuntu to notice they are both their at the same time and set up the dual monitors, this is the only thing stopping me moving from XP full time as I really need the extra desktop space.

If anyone can help me with regards to setting up dual monitors, with these two different cards, it would be appreciated. I am willing to run 8.10 if need be for this.

---

### Post by intel352 on 2009-08-21
Did you ever get this worked out?

Have similar situation, onboard ATI, PCI Nvidia, would like to get dual monitor working across both as well

---

### Post by markbuntu on 2009-08-21
I don't think you could get nvidia and ati to play together at least with the proprietary drivers. Their proprietary drivers replace many parts of the xserver so they are mutually incompatible. 

You could maybe do it with the generic VESA driver but it is fairly basic and very limited in its capabilities.

You might be able to use the open source drivers but you would probably need a research grant to figure that out.

---

### Post by DylanH on 2009-08-21
Similar to my situation. Seems to be a common problem? 
[http://ubuntuforums.org/showthread.php?t=1246419](http://ubuntuforums.org/showthread.php?t=1246419)

---

