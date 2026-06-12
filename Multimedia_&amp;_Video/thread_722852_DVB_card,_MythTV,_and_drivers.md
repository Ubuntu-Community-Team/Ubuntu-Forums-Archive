---
title: "DVB card, MythTV, and drivers"
date: 2008-03-12
forum: Multimedia &amp; Video
---

### Post by rico4295 on 2008-03-12
I'm running gutsy 7.10, mythtv 0.21, and a twinhan 102g dvb card. the kernel loads its own driver for the card whose version  is 0.9.17 which does detect and sometimes operates the card. After some reading I believe video4linux makes these drivers for dvb devices. I've install their latest driver and do  see more info in `dmesg`. Although I'm still seeing the 0.9.17 driver being loaded. 

The issue I'm having is after the pc has been shut off I don't get a signal when I use the dvb card in mythtv UNLESS I boot into xp and run the tv app, works fine, then restart and boot back into linux.

I would like to use a new/newer driver that operates the card correctly. I'm not sure the driver I installed made any difference or even if it's being used. I am wondering if it's a driver problem or a hardware problem. If it's a driver problem would I be looking at having to compile my own kernel to solve this?

Any thoughts or ideas would be great

---

