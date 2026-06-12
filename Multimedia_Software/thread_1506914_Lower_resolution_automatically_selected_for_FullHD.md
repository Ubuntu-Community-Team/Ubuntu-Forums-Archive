---
title: "Lower resolution automatically selected for FullHD HDTV"
date: 2010-06-10
forum: Multimedia Software
---

### Post by ePierre on 2010-06-10
Hi!

I've recently got a HDTV LCD display (BenQ SD3742), and a nettop (Acer revo 3610) to go with it. I connected them using an HDMI cable, and I installed the latest Ubuntu 10.04 64 bits edition.

I then installed the latest nvidia drivers (nvidia-current package, which is nvidia-glx-195) to support nVidia ION platform using this ppa: [https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

According to various websites, my LCD is FullHD, so I should be able to select 1920x1080 resolution. But the automatically selected resolution is 1280x768, and in nVidia configuration panel, this resolution is stated as being "native resolution" for my screen (its name is correctly detected by Ubuntu, by the way!).

If I select 1920x1080 and "Apply", the resolution is changed but the borders of my desktop are not available... and the image looks deformed anyway.

Is there any way to make Ubuntu to detect properly this LCD display in its real native resolution (FullHD, 1920x1080)?

Thanks in advance!

---

### Post by ePierre on 2010-06-11
OK, a friend of mine brought his PS3 and we tried to connect it to my TV, and we can play in 1080p, so my TV is, indeed, fullHD...

I don't know why Ubuntu/nvidia sees my screen as "1280x768".

I also tried xrandr, and the max resolution is 1280x768 :(

---

### Post by ePierre on 2010-06-11
Problem solved...This morning I startd my revo, went to the nVidia options and selected the corect resolution, and it worked!

I probably forgot a reboot or something...

---

