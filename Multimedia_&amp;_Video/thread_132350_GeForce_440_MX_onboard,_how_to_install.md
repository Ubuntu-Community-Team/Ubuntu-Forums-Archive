---
title: "GeForce 440 MX onboard, how to install?"
date: 2006-02-18
forum: Multimedia &amp; Video
---

### Post by yootje on 2006-02-18
I tried numerous linux distro's, and the one thing I always get stuck on is the drivers for my nVidia card. This time I want to do it right. Can someone please tell me what I should do to get my drivers right (I have an onboard nVidia GeForce 440 MX videocard)?  I use Ubuntu 5.10. Thanks in advance!

---

### Post by ngms27 on 2006-02-18
Just use Synaptic to install Nvidia-Glx

JonnyT

---

### Post by yootje on 2006-02-18
Okay, I did that, but I still have a maximum refresh rate of 60Hz (I'm getting headache already). The nVidia logo appeared when I restarted X.

---

### Post by Denta on 2006-02-18
Then the driver is installed and running. Take a look at your /etc/X11/xorg.conf to have more refresh rates.

---

### Post by yootje on 2006-02-18
I did this and now I have a refresh rate of 85 Hz, at 1024x768...

On my Windows installation I have a refresh rate of 80Hz at 1600x1200. I can't pick 1600x1200 with Ubuntu. Help is much appreciated :)

---

