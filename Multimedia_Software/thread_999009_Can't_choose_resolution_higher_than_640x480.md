---
title: "Can't choose resolution higher than 640x480"
date: 2008-12-01
forum: Multimedia Software
---

### Post by Dark_Sabre on 2008-12-01
I just installed kubuntu 8.10 yesterday, however, whenever I try to change the resolution to higher than 640x480, the system freezes up. now I am new-ish to linux as my computer has never let me install it. My graphics card is a radeon 9200 128 mb.

---

### Post by tilerwen on 2009-01-14
Edit your xorg.conf file with 
Section "Device"
   ...
   Option "IgnoreEDID" "1"
EndSection

---

