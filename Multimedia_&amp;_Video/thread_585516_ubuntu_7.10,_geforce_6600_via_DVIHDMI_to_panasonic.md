---
title: "ubuntu 7.10, geforce 6600 via DVI/HDMI to panasonic hdtv"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by hithere27 on 2007-10-21
hi,

i want to connect my ubuntu pc via an dvi->hdmi cable to my panasonic 42" plasma full hd tv.
i cant get 1920x1980 resolution to work. driver seems okay, i get a picture but its all ****** up, no matter which resolution i try. seems like i cant turn it bigger than 1280. my tv´s description says its 1920x1080 full hd, so im thinking if the gfx card is the problem or the driver itself.
2nd weird thing is, i can only get a clear picture of the ubunto desktop if its set to 24Hz, not 50 or 60. but even with that, the task menu are cut and i dont have a real full screen.

tried serveral settings in xorg.conf but no luck. can anyone help ?

---

### Post by hithere27 on 2007-10-22
bump

---

### Post by nnylyart on 2007-10-28
I have the exact same problem running a GeForce 7800GS and a Panasonic PT-44LCX65 44 in. It displays 1280 x 720 pixels  fine but it doesnt really fit the screen.  In windows using the Nvidia control panel I could customize the resolution to be 1200 x 676 which fits perfect.  I have tried a lot of xorg.conf settings and none seem to make any difference.  I wish I could find a solution to this because I am stuck using Windows for now :(

---

### Post by C@bb@ge on 2007-10-31
native resolution of an hdtv is 1360 by 768 if the tv is 1080i, if the tv is 1080p then it will be 1900 by 1080, but the majority of hdtvs are 1080i at the moment, thus 1360 by 768 should be spot on for you.

---

### Post by C@bb@ge on 2007-10-31
native resolution of an hdtv is 1360 by 768 if the tv is 1080i, if the tv is 1080p then it will be 1900 by 1080, but the majority of hdtvs are 1080i at the moment, thus 1360 by 768 should be spot on for you.

---

### Post by lukemack on 2008-07-05
Did you resolve this? I can view 1280 x 720 but this should be 1360 x768 and I can't force this in nvidia-settings or xorg.conf. The gnome panels are only half showing which is a real pain.

---

