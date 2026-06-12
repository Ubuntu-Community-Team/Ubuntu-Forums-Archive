---
title: "PCTV T290e DVT-T2 USB  - no channel scan [solved]"
date: 2012-02-15
forum: Mythbuntu
---

### Post by vagster on 2012-02-15
Hi All,

I have added PCTV T290e DVB-T2 tuner into my existing mythtv setup. I re-built v4l using the [media_build]("http://git.linuxtv.org/media_build.git") script. 

On reboot, I got all the correct modprobe results, lsusb etc. Everything suggested that the card was working correctly. However, when I did a channel scan in mythtv, it would not find any channels.

This baffled me for a while before I checked the back of my machine and found I had plugged it into a USB3 port by mistake. When I swapped it back to the USB2 port, everything worked fine.

Not sure why this is but I thought I would post it here so that, if anyone encounters this issue, they check the USB port first!

Cheers

Stephen

---

