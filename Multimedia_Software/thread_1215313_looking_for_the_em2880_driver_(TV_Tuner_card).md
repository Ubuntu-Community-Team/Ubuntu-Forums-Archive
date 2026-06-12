---
title: "looking for the em2880 driver (TV Tuner card)"
date: 2009-07-17
forum: Multimedia Software
---

### Post by Stochastic on 2009-07-17
So I just got a new Huappauge WinTV HVR 950 and am attempting to get things working on my Ubuntu machine.  After googling, and googling, and package searching, and attempting to get things up and going, I've thrown up my arms.

It seems like the missing piece I need is the em2880 driver but the mercurial repository that all the howtos point towards has been emptied (about 5 weeks ago).  If anyone knows where I can find an old copy of that driver I would be very grateful.

Or if I am going about this the wrong way, please let me know.  On a Jaunty 9.04 machine.

---

### Post by gm_w on 2009-07-17
I followed these steps to setup my HVR 950 usb tv tuner on Ubuntu 9.04 Jaunty:


wget [http://www.steventoth.net/linux/xc50...25271_WHQL.zip](http://www.steventoth.net/linux/xc50...25271_WHQL.zip)
unzip -j HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip Driver85/hcw85bda.sys

sudo apt-get install linux-headers-generic

cp /usr/src/linux-headers-`uname -r`/Documentation/video4linux/extract_xc3028.pl ~/HVR950
chmod +x extract_xc3028.pl
./extract_xc3028.pl

sudo cp xc3028-v27.fw /lib/firmware

Tvtime is able to recognize the device and is producing great video. But the problem is no audio at all...

can anyone help with the sound issue?

---

### Post by Stochastic on 2009-07-17
I've done this already (you gave a broken link though, it should be [http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip](http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip) but I'd already walked through the steps so no worries).  TVtime just gives me a blue screen that says cannot open capture device /dev/video0 (even when run as sudo).

What could I be doing wrong?  I'll try it on my Karmic install later tonight to see what's up...

---

