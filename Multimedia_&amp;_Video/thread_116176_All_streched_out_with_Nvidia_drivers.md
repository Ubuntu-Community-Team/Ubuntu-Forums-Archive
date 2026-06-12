---
title: "All streched out with Nvidia drivers"
date: 2006-01-12
forum: Multimedia &amp; Video
---

### Post by naruto11111 on 2006-01-12
Hi, I'm new to linux.  After installing ubuntu5.10, there were two black bars, one above and one below the top and bottom toolbars.  (Made it look like my Desktop was a widescreen movie playing on a 4:3 tv.

I installed the nvidia drivers following the tutorial on this forum.  

It seemed to work fine, the black bars are gone, but now it appears everything is a little too streched up and down.  Text is slightly thinner than it should be and so I downloaded a picture of a perfect circle and confirmed that things are streched.

I couldn't find how to remedy this in the NVIDIA X Server settings menu.  Does anyone know how to fix this?  Thanks in advance.

-Michael

---

### Post by MartinG on 2006-01-12
Sounds to me like the system is confused over screen resolutions. Check your display settings, and maybe also run```
sudo dpkg-reconfigure xserver-xorg
```Especially make sure the right resolutions are picked.

---

### Post by Thirsteh on 2006-01-12
Sometimes you have to manually adjust the monitor using the physical buttons on the monitor. Click "System->Settings->Monitor Resolution" and see what resolution you are running --- you should really be running one of the following: 800x600, 1024x768, 1280x1024 or 1600x1200 -- if you're running something like 1152x768, you should change it :)

---

