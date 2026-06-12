---
title: "New to Ubuntu: Need help with resolution and dual monitor setup"
date: 2008-11-03
forum: Multimedia Software
---

### Post by Aldyrin on 2008-11-03
Well, I finally got Ubuntu working on my computer yesterday, so I'm pretty new to all this.  I'm working with a completely fresh install here, no changes made other than downloading updates and changing the resolution to the highest available.

I went to change the resolution of my primary monitor (Dell 2405fpw), and I did not see a setting available for 1920x1200.  Any suggestions there?  

My display hardware is the following:
Primary Monitor: 2405fpw (connected via DVI)
Secondary Monitor: 1080p projector (1920x1080 max resolution) (connected via DVI)
Video card: x1900 series ATI card

I would like to set up the following:
-1920x1200 display on my primary monitor
-1920x1080 display on my secondary monitor (extended desktop, ideally)

I need to be able to watch video from totem or vlc or whatever in either monitor.  

Thanks in advance!

---

### Post by Bender2k14 on 2008-11-03
Sadly, dual monitor support and graphics in general is better with Nvidia than ATI.  After I switched to linux a year and a half ago, I bought an Nvidia card to replace my ATI card.

When I had my ATI card, I was able to get dual monitor working by following [this thread]("http://ubuntuforums.org/showthread.php?t=221174"), but only after several hours of trial and error.  I think I used Xinerama, but I am not sure now.

Also, I think X.Org changed somewhat in how it handles configuration, so pre 8.10 tutorials for dual screen/monitor with ATI cards might be outdated.

While waiting for another reply to this thread, try searching Google for tutorials on how to get dual screen/monitor in Ubuntu 8.10.

---

