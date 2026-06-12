---
title: "asus s96s"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by hhpeter on 2007-10-28
I have a asus s96s laptop with integrated webcam and mic 
is there a way to make them work in ubuntu 7.10 ?
Everything else is working nvidia 8600gs is working very good compiz is working wireless is working....

---

### Post by hhpeter on 2007-12-20
bump anybody got this webcam to work 174f:6a51
please help me

---

### Post by RobotJox on 2008-03-21
bump - same problem and setup here

---

### Post by bensexson on 2008-03-22
I have an ASUS S96S as well I used this how-to to get the webcam working:
[http://www.zer0.net/2007/12/asus-syntek-webcam-installation-on.html](http://www.zer0.net/2007/12/asus-syntek-webcam-installation-on.html)

---

### Post by bensexson on 2008-03-22
If your video is flipped you will need to add options stk11xx vflip=1 hflip=1 to /etc/modprobe.d/aliases

---

### Post by nikola.borisof on 2008-04-18
What exactly should i add to this /etc/modprobe.d/aliases file to make the video flipped back to normal. Also where should i add this stk11xx.ko file right now i have to run the following sh script every time i want to use the web cam. 

#!/bin/bash
cd /home/nikola/Software/Cam/stk11xx-1.3.1/
sudo insmod stk11xx.ko
echo 1 > /sys/class/video4linux/video0/vflip
echo 1 > /sys/class/video4linux/video0/hflip

Thanks Nikola

---

