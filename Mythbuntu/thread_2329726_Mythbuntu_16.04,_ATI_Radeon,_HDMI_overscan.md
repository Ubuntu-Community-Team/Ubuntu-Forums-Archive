---
title: "Mythbuntu 16.04, ATI Radeon, HDMI overscan"
date: 2016-07-04
forum: Mythbuntu
---

### Post by manuel_acs on 2016-07-04
Hallo,

how can i disable the overscan with the standard radeon driver for my ATI? 
with the old fgrlx and the amd util it was done after a few klicks.

Specs/connection:
Asus MB with AMD E-450 with integrated Radeon HD 6320 graphics card (Desktop set at 1920x1080 Full HD) --> HDMI --> Denon AVR (input signal is 1920x1080 Full HD) --> HDMI --> LG LCD TV (input signal is 1920x1080 Full HD)

... and no - i will not let the AVR nor the LCD do any up/down scale

when i set xrandr .... overscan off, the picture is to small (~ 1.5 cm on each side)
when i set my tv to "Just Scan", the picture will fit
... both are no solutions!

all my other devices connected with HDMI (including NB with Ubuntu 14.04) provide a perfect picture out of the box

thanks for any hints or a clean solution :)

greetz
Manuel

---

### Post by khPWXxF on 2016-07-04
Is there a setting on your TV / monitor?  On my Samsung it was picture size set to "screen fit"
Phil

---

### Post by wayne36 on 2016-07-05
On my LG TV (identified as a different sized Goldstar by mythbuntu)  "just scan" in the video setup fixed my issue.

---

