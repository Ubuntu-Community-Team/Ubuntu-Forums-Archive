---
title: "Multimedia Computer Display Issues"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by initialdrifteg6 on 2008-02-27
I have a AMD 2000+ machine that is powered by a GeForce4 (8x AGP) Ti-4600 connected to an RCA HDTV via DVI-D cable. I currently an stuck in the 640x480 resolution and can't change it. I looked at the display configurations to change the monitor type, but even the 1280x720 resolution won't set in. There is also an overscan issue right now which will hopefully go away with the proper screen resolution. My version of Ubuntu is 7.10.

Thanks for your support and help!

---

### Post by wolfen69 on 2008-02-27
open terminal and
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
once the configuration utility begins, use the space bar to select/deselect

---

### Post by Yellow Pasque on 2008-02-28
Have you installed the nvidia proprietary drivers? If not, I would recommend a program called Envy, which automates a lot of the process for you.

---

### Post by initialdrifteg6 on 2008-02-28
I got the drivers working properly on a 17" LCD before transfering the node to the tv room. So the restricted drivers were working properly. Ill try that command.

---

