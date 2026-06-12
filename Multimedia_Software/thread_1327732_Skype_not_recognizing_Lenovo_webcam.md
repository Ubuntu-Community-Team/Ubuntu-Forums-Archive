---
title: "Skype not recognizing Lenovo webcam"
date: 2009-11-15
forum: Multimedia Software
---

### Post by @tticus on 2009-11-15
Hi,
  I have a Lenovo webcam and I cannot get Skype to recognize it. 
I have recently upgraded to Ubuntu 9.10 and everything worked on 8.04. I know gspca is build into the kernel, I have also installed xawtv and it recognizes the camera. 
However, when I start Skype, it sees the camera, but it does not work properly (green screen all the time). I have given my /dev/video0 777 priviliges, and it still does not work.

Did anybody experience similar problems ?
Could somebody help me ?

Thanks,
  atticus

---

### Post by vonOBelix on 2009-11-30
I have the same Problem on Karmic 64Bit. Cheese, Mplayer, VLC, Ekiga have noc problems with my LenovoCam but Skype just shows weird (mostly green) pictures.

---

### Post by @tticus on 2009-11-30
This line of code fixes my problem :
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

---

