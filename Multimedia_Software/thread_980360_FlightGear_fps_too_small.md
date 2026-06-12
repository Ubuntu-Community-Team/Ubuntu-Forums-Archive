---
title: "FlightGear fps too small"
date: 2008-11-12
forum: Multimedia Software
---

### Post by kriukov on 2008-11-12
I have Ubuntu 8.04 on both of my computers (desktop AMD Athlon 2 GHz / 3G RAM (I use i386 Ubuntu on it) with ATI video card and laptop Dell Inspiron 1525N Intel Pentium 2 GHz / 3G RAM with on-board Intel graphics card). When I use FlightGear on the desktop computer, the fps varies at about 10-12 fps. However, on the laptop it is significantly lower. It was 2-4 fps, but I found this:

[https://bugs.launchpad.net/ubuntu/+bug/252094](https://bugs.launchpad.net/ubuntu/+bug/252094)

and added

 Option "XaaNoPixmapCache"
 Option "XAANoOffscreenPixmaps" "1"
 Option "DRI" "true"
 Option "AccelMethod" "XAA"

to the Device section of xorg.conf, after which I got 6-8 fps.

Surprisingly, both computers list fps of thousands (laptop even bigger) when I do "glxgears -display".

Is my problem flightgear-specific? What else could be the obstacle? I have heard people report 50-60 fps on their flightgear.

---

### Post by hchizkool on 2008-11-14
hi ive just installed flightgear on my HP530 using 8.10 and i can start it up but when it gets toinitializing subsystems it just blinks off with no warning. can anyone help?

---

### Post by LucidLoon on 2009-02-01
******I found that hitting [shift] f10 increased my framerate. It changes the menu style.

---

### Post by tuxxy on 2009-02-01
glxgears is not a reliable FPS monitor and can be easily increased by the user.  FLightgear runs fine for me although hardly any games would run good for me when I used ATI videocards

---

### Post by bba1973 on 2009-02-07
Getting about 8 FPS average with my Gateway laptop. It's got an Intel GMA 950 with up to 224 MB shared video memory with 4 GB of RAM. With Vista, it ran Rainbow Six 3 really well, so it should be able to get more than 8 FPS out of FlightGear. Any ideas? The menu thing isn't helping much.

---

