---
title: "Nvidia geforce2 MX200"
date: 2008-09-09
forum: Multimedia Software
---

### Post by psyXas on 2008-09-09
Hello,
i have installed dreamlinux 3.3 and nvidia driver from easy install, when computer restart - i can see nvidia logo and can configure nvidia-settings, but when i want to play flash games - it works very slowly like 1 frame per second. So it is video driver problem or not? My video card is nvidia geforce2 MX200. I think, that it maybe openGL(in windows) problem or smth else.

So i install ubuntu 8.04 on my computer - same problem :( What can i do?

I can download from nvidia site only 71.86.04 driver version, because higher version don't support my video card. Maybe i must install ubuntu 7.04 or lower version? 

P.S. sorry for my english :(

---

### Post by cdtech on 2008-09-09
Try installing "envyng-gtk":
```
sudo apt-get install envyng-gtk
```
Then run the program to install the latest driver for the nVidia card.

---

### Post by lovinglinux on 2008-09-09
> **cdtech said:**
> Try installing "envyng-gtk":
```
sudo apt-get install envyng-gtk
```
Then run the program to install the latest driver for the nVidia card.

Probably won't work. Geforce2 series is 8 years old, so newer drivers don't support it.

> **psyXas said:**
> Maybe i must install ubuntu 7.04 or lower version?
 I'm not an expert, but I guess it won't make any difference, since Flash player will be the same version.

---

### Post by tuxxy on 2008-09-09
If you plan to upgrade also go with a new nvidia

---

### Post by lovinglinux on 2008-09-09
Another possibility is to try the onboard video card. Since you are not trying to run 3D games, maybe the mobo is more compatible with flash (someone p&#314;ease correct me if I'm completely wrong).

---

### Post by psyXas on 2008-09-09
install nvidia driver using envyng-gtk - all works fine and openGL, but flash  games works still 1 frame per second. Maybe it's flashplayer problem?
Thanks for answers :)
i'm trying on this game [http://x.gametop.com/free-online-games/monster-truck-rampage/play.html](http://x.gametop.com/free-online-games/monster-truck-rampage/play.html)
P.S. sorry for my english

---

