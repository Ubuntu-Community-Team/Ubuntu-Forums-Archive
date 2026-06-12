---
title: "Full Screen video lag?"
date: 2012-07-28
forum: Multimedia Software
---

### Post by bdfull3r on 2012-07-28
Intel i3 Sandy Bridge
4GB RAM
Zotac Ion Gt218 graphics card
Ubuntu 12.04 LTS 64bit

I have a dual boot computer with windows 7 and ubuntu. When i want to watch video from either a live stream or a youtube video, it lags horribly when i go full screen. Not like 60fps down to 30fps, more like 30fps to 20 frames a minute. It is completely unwatchable. 

Normally i would think my graphics card is too weak or doesn't have the latest drivers. Nope, drivers are up to date. I tried the ones the system found on the setup, i tried the ones straight from NVIDIA, i also tried the one that showed up under additional drivers menu.

The kicker is when i boot into windows 7, there is no lag. Why does the Ubuntu (and previously Linux Mint) side of the my computer lag on full screen video?

---

### Post by mscout2004 on 2012-07-28
Did you do the most recent updates for flash?

---

### Post by bdfull3r on 2012-07-29
> **mscout2004 said:**
> Did you do the most recent updates for flash?

Yes Flash is up to date, but its not just a flash related issue. HTML5 video lags at full screen as well on Ubuntu but not on my Windows side

---

### Post by Kreaninw on 2012-07-29
First, Adobe Flash Player on Linux/Ubuntu isn't HWA(Hardware Acceleration) enable. In short, it doesn't use your GPU to help with processing work like on Windows. No matter what GPU you're using, NVIDIA or AMD/ATI. So, Flash on Linux == SLOW.

Secondly, all web browsers on Linux/Ubuntu also effect with the same issue, your GPU is there, driver installed, but it just doesn't do a thing. While in Windows it's HWA enabled on all browsers >>> IE9, Firefox, Chrome, Safari, Opera(not by default).

I don't know for sure that HTML5 video in the browser has anything to do with HWA. Currently, only Opera 12 for Linux can use HWA feature, but it isn't enabled by default. I'm using it for a while now, still didn't found any bug.

[http://my.opera.com/desktopteam/blog/2012/04/20/update-on-hardware-acceleration-in-opera-12](http://my.opera.com/desktopteam/blog/2012/04/20/update-on-hardware-acceleration-in-opera-12)

---

