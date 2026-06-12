---
title: "does HDMI audio work on ATI Radeon HD 3200"
date: 2008-12-31
forum: Mythbuntu
---

### Post by jeremycobert on 2008-12-31
hey  guys,
is hdmi audio working with ATI mobo's ? i cant seem to find the answer. i picked up this mobo

[http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=3672390&cm_mmc=Email-_-WebletMain-_-WEBLET03SHIP-_-03ship&SRCCODE=WEBLET03SHIP](http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=3672390&cm_mmc=Email-_-WebletMain-_-WEBLET03SHIP-_-03ship&SRCCODE=WEBLET03SHIP)

the board has ATI Radeon HD 3200 Graphics which  worked well with generic drivers (no audio) and i installed the restricted ati drivers and they worked as well, but still no audio. mythtv does not open correctly, but i think i found the answer to that.

before i go any further i want to make sure im not chasing something that does not work. so if anyone can confirm that this setup work, i would be most grateful.

---

### Post by jape42 on 2008-12-31
HDMI audio works well for the 3200 with the radeonhd x11 video driver, BUT the 3200 does not yet have video acceleration. I can playback at 640x480, but definitely not at 1920x1080 on my AMD X2 5200.

The good news is that AMD just released information needed to add 3d video acceleration support for the HD3200 and other GPUs.

Here's some more info:

[http://ubuntuforums.org/showthread.p...highlight=hdmi](http://ubuntuforums.org/showthread.p...highlight=hdmi)

regards

jp

---

