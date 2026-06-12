---
title: "Unable to get two ATI Radeon HD 5700 cards working across 3 monitors"
date: 2011-08-16
forum: Multimedia Software
---

### Post by ChrisStockton on 2011-08-16
I am unable to get everything working under ubuntu 11.04. I have tried both the default restricted drivers, as well as the latest and greatest drivers from the ATI website (which I don't reccomend, they caused my computer to reboot and give me "sync overflow errors" at my bios screen.

I am able to get all 3 monitors detected, but soon as I enable xinerama I start getting black screens.

Reproduce (from memory):
  Fresh 11.04 install
  aticonfig --adapter=all --initial=dual-head
  Open ati catalyst, turn on xinemara

Result:
  Screen does not turn on once I log out and log back in and the mouse doesn't move either, just black screens. At that point I can ALT+CTRL+F1 into a terminal and reset my xorg/reboot and get back to ground zero.

My setup:
  Radeon HD 5700 x2
  1 x 24 inch led on hdmi
  2 x 22 inch led on vdi
  
  Less relevant system specs, 8gigz ram, AMD Phenom, good specs

Has anyone had luck with a ati 2 card 3 monitor setup?

-Chris

[EDIT]
At this point after all the fuss with the ATI Drivers I experienced, specially the drivers from their website crashing my system, I am open to buying any recommended nvidia cards people have working easily in 3 monitor setup.

---

