---
title: "Microsoft LiveCam 1000 driver"
date: 2009-09-09
forum: Multimedia Software
---

### Post by Qwertyop on 2009-09-09
***I do not want to use wine for this, I may as well use windows vista!***

I purchased a Microsoft LiveCam. Seeing as the name is *Microsoft* and knowing how to use google, I knew before I purchased this that the camera could not be used with linux. But it was a cheap camera and good for its price so I got it (I am going to Uni now and I want to video call home). I can use this camera on Windows fine, and I can easily boot windows when I want to call home/use it, but I'll much rather use it on Ubuntu.

Looking at what others say, they have got this camera working but they do not really say how they got it done... can anyone help me?

lsubs says:
```
Bus 001 Device 002: ID 05ac:1263 Apple, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 002: ID 045e:00f7 Microsoft Corp. LifeCam VX-1000.**
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Thanks a lot.

---

### Post by jesterthejedi on 2009-09-18
I have this cam. It took me a long time, 6 months to get the right driver up and working. You have to reinstall after each kernel update! 

Do this:
Download driver:
[http://linuxtv.org/hg/~jfrancois/gspca/](http://linuxtv.org/hg/~jfrancois/gspca/)
grab the .bz2 file - located on the left bar
extract and change directory
in terminal type these commands no quotes:
"make distclean"
"make clean"
"make menuconfig" - choose the gspca/sonix, exclude others
"make"
then type "sudo make install"
reboot

tested working on Intrepid With Cheese, Ekiga, Skype, GyachE, Xawtv

COLORS are fine! no more green/blue mess.
Camorama, Kopete, and Skype require:
"LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype(or alt)"

---

### Post by stanca on 2009-10-07
Works for me too again after 2 months almost.:P
You can do just this:
> sudo apt-get install subversion build-essential linux-headers-$(uname -r) && wget [http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2](http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2) && tar xf tip.tar.bz2 && cd gspca-* && make && sudo make install && sudo depmod -ae $(uname -r) 
Wait,reboot and bring the beer.;)

---

### Post by Qwertyop on 2010-02-14
Thanks guys, I've been using my cam for a while now but can't get it to work with flash, any suggestions???

I use to switch to Windows to when I need to use my cam (on a dual boot but ubuntu) messed up that partition recently (I know the problem and it is easily fixed with chkdsk but I don't have a CD drive).

Any suggestions on the two problems? Thanks.

---

### Post by no2498 on 2010-02-15
i do NOT have mine working with flash yet

but you may need to do a
if flash so
the same thing they say for skype

im at a loss for the whole command for it

i can get green bars on mine on a flash site with 910 
mine is a NON UVC cam used the old v4l1 driver

we now use v4l2 
or so they say

also you may need to allow and remember in the adobe settings manager

---

