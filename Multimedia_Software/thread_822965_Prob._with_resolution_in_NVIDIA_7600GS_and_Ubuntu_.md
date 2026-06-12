---
title: "Prob. with resolution in NVIDIA 7600GS and Ubuntu 8.04"
date: 2008-06-08
forum: Multimedia Software
---

### Post by stell on 2008-06-08
I am very new to Ubuntu, and it's driving me nuts that I can't get the resolution above 800X600 and 61hrtz. I have a monitor ( 2 actually) that support 1024X768 and would love any help I could get!!!!

Stell

---

### Post by jp734 on 2008-06-09
Check if you have a resolution higher than 800x600 specified on your xorg configuration file? (/etc/X11/xorg.conf)

Open Terminal and type the command:
sudo gedit /etc/X11/xorg.conf

If need help with configuration, please post the file.

---

