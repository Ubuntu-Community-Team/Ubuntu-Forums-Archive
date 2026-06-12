---
title: "Need Help with Graphics Display"
date: 2008-05-08
forum: Multimedia Software
---

### Post by sanjeevpunj on 2008-05-08
[SOLVED]I managed to do it once before, but I forgot how I did it,and my HDD crashed due to bad sectors, so I am onto it again with a fresh install of UBUNTU 8,04. and so I need help to get back the resolution I want to work with. 
I have a NVIDIA GT7300 Graphics Card, and I have driver (nvidia-glx-new) already downloaded, but I get only two resolutions:-640x480 and 320x240. 
My XORG.CONF FILE is empty!!!

How do I get back the XORG.CONF file?

How do I resume working in a normal (1280 x 1024) display mode? 

help help help!

---

### Post by ubuntu-freak on 2008-05-08
Press Alt F2, type in:
 
**gksudo displayconfig-gtk** 
 
Type your password and execute, then select your resolution. 
 
Nathan

---

### Post by sanjeevpunj on 2008-05-09
Thanks! It worked though I used another way to reach the same application :-

/usr/shares/applications/screen and graphics 

I just opened this application and selcted the monitor and reslution i needed.

---

### Post by ubuntu-freak on 2008-05-09
> **sanjeevpunj said:**
> Thanks! It worked though I used another way to reach the same application :-

/usr/shares/applications/screen and graphics 

I just opened this application and selcted the monitor and reslution i needed.

 
Hmm....whatever floats your boat. :-)
 
Nathan

---

