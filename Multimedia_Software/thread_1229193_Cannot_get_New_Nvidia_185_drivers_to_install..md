---
title: "Cannot get New Nvidia 185 drivers to install."
date: 2009-08-01
forum: Multimedia Software
---

### Post by k4kelly on 2009-08-01
I'm new to Linux about 6 weeks now.  I tried for 2 weeks to get Nvidia drivers to work and  gave up for a while. I seen the new drivers NVIDIA-Linux-x86-185.18.14-pkg2. I've tried the 180 version several time and 71. I get them isstalled but when I reboot only get terminal mode. I tried to load the 185 ver but get Unknown ID: message. I need some help
to get around this problem.

---

### Post by tipii on 2009-08-01
I have a similar problem in that the install deceptively seems to go ahead without a hitch.
After I install the Nvidia drivers (before doing anything else) and log off, tty7 fails to reload. I have tried drivers 185, 180 and the one before that.
When restarting I am automatically promted to log into tty1 and when I chvt 7 I am greeted with a black screen and a dismal flashing cursor.
I have tried reconfiguring the xserver-xorg and reverting to failsafe xorg.conf.

---

### Post by Arup on 2009-08-01
Have you removed linux restricted modules

---

### Post by tipii on 2009-08-01
I just removed them but still have the same problem.
T

---

### Post by tipii on 2009-08-02
I've since tried Ubuntu 8 and got the same problem. I am beginning to think it is something to do with my system... I am running two widescreen monitors (at different resolutions) and two sli graphics cards (GTX 260's), with the monitors plugged into one only. Everything works fine until I install the NVidia drivers. Can anyone help?

---

### Post by k4kelly on 2009-08-02
I removed the nvidia drivers " sudo apt-get --purge remove nvidia*" and tried to install again but still have the same problem. Unknow ID:

---

