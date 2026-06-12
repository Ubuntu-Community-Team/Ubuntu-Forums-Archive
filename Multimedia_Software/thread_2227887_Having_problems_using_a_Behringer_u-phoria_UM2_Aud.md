---
title: "Having problems using a Behringer u-phoria UM2 Audio USB int with Jack and Gutirixt"
date: 2014-06-04
forum: Multimedia Software
---

### Post by DavidNewman on 2014-06-04
Hello,  
I am using Guitarix,Jack and a Product from Behringer UM2. I cannot get them to work together I have postd some diagnosis stuff on the page. 
lsusbdavid@david-HP-2000-Notebook-PC:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b249 Chicony Electronics Co., Ltd 
Bus 003 Device 006: ID 08bb:2902 Texas Instruments Japan PCM2902 Audio Codec
 ALSA
Lists is under /proc/asound as usb audio; usb audio playback 1; capture 1
 Guitarix doesnt see it at all.

---

### Post by Bucky Ball on 2014-06-04
Welcome. Are you using Ubuntu Studio or Ubuntu? Which release?

---

### Post by DavidNewman on 2014-06-04
I am using Ubuntu 12.04.

---

### Post by DavidNewman on 2014-06-05
I have upgraded to xubuntu 14.04 and am still having problems, the ALSA interface recognises it but it doesnt seem to go through Jack.
I am a newbie at Linux and need help badly.

---

### Post by Bucky Ball on 2014-06-06
Please do not post duplicates. Your last two posts have been jailed. Feel free to bump your thread every 24 hours with simply 'bump' or any new info that comes to hand at anytime. 

Repeating yourself will not get you anywhere ...

---

