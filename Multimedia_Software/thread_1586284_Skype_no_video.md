---
title: "Skype no video??"
date: 2010-10-01
forum: Multimedia Software
---

### Post by TheKeyMaker on 2010-10-01
Hi Everyone...

I have this problem that I am trying to fix now and nothing seems to be working...

I am trying to get my web-cam working with skype

Information:
Linux Mint 9 distro
Webcam works under cheese and Ekiga 
I have tryied multiple webcams lsusb( ALI Corp. Video Camera Controller, LifeCam VX-6000)
Skype 2.1.0.81
Any ideas on how to troubleshoot skype???

---

### Post by Beta_Grumm on 2010-10-01
Maybe take a look through their lists of supported / not supported. 

[https://wiki.ubuntu.com/SkypeWebCams]("https://wiki.ubuntu.com/SkypeWebCams")

Since skype for linux is still in beta it would be difficult to actually bug that out. Most likely skype just isn't supporting it yet for whatever reason that is unfixable until they get tie up some beta ends. I would try a cam on their "deffinitely works". See if that grants you any luck.

---

### Post by no2498 on 2010-10-02
put this in a terminal see if skype works

LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype

---

