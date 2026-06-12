---
title: "Devede Finished DVD Choppy Playback"
date: 2007-02-22
forum: Multimedia &amp; Video
---

### Post by iceman504 on 2007-02-22
im pretty new to using devede so after converting two avi files to dvd format for one movie i burn it to a dvd and the sound is perfect but the video is choppy. I have tried buring w/ k3b, Gnombaker, and brasero all with the same result. I thought the burn speed was too high so i set it to 2x and still got the same thing does anyone know whats going on?

---

### Post by DennShin on 2007-02-24
I am having the same problem.  3ghz p4 2gb of memory source file is being converted and stored in the home directory. and burned with the right click + Write to disc option.  Any idea's?

Ok I just burned the .iso with K3B and I think I found the problem.  My FIFO buffer was running at about 8% with an occasional jump to 100%.  My device buffer was not readable, although k3b detected the correct max run speed the dvd was burning at speeds of about 5 - 8x.  Max is 16.  My question is.  Was my DVD Rom drive not installed properly during installation?  Is their any other way to check besides buring coasters? My drive is a "Sony DVD RW DRU-810A".  

Thank you for any help.

---

### Post by DennShin on 2007-02-26
Bump

---

### Post by iceman504 on 2007-02-27
ok i fixed my problem after going through a good amount of dvds...i booted up my windows xp in vmware and installed nero 7(nero express) and used it to burn a couple of dvds w/ the same result so i checked to see  if data was being written correctly to the discs by looking at the data side which i noticed their was swirly marks and data written almost like it stopped burning for a little while and then started again.....So i reduced the speed to 2.4x (lowest setting for me) and burned anotha disc, looked at it again and this time the data was written correctly. I do remember trying this on ubuntu but it didnt fix anything so i will try it again on ubuntu in a few of hours

---

