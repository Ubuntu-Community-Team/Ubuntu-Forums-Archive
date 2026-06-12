---
title: "internal mic not working on hp dv6000"
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by Llewxam on 2008-03-30
i've been trying to find a solution for this. the internal mic on my hp laptop used to work perfectly before. sometime after i realized the headset jack didn't so i followed a thread to resolve that issue. wasn't until yesterday i found the mic not working. 
volume preferences shows an internal mic slider and it is in 100, but still no capture of sound. the chipset when running alsamixer on terminal displays this: Conexant CX20561 (Hermosa)

also, searching for that chipset on both forums and google yields no results. so if there is any one out there who can help me with this issue please. 

to add: the alsa driver version is 1.0.14

---

### Post by pseudo-random on 2008-03-30
I did a lot of trial and error to get my mic working with alsamixer.
In the recording window I tried just about every combination of muting with the spacebar and/or amplifying other sources until it worked. Perseverance paid off :)

---

### Post by Llewxam on 2008-03-30
yea i keep tweaking around and playing with every setting i can get but nothing seems to work. >.< it's getting on my nerves.

---

### Post by xc3RnbFO8P on 2008-03-30
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller")

Method J: Installing alsa-driver-1.0.16rc1

    *

      does work: HP dv6000 (64 bit)
    *

      does not work

Just download and build the new alsa driver and it works.

wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16rc1.tar.bz2)
tar xvpjf alsa-driver-1.0.16rc1.tar.bz2
cd alsa-driver-1.0.16rc1
./configure --with-cards=hda-intel
make
sudo make install

Solved:

    *

      Audio & internal mic. works

Remaining problems with this method:

    *

      Headphones do not mute the speakers (which were indeed different channels in other distros)

---

### Post by Llewxam on 2008-03-30
Remaining problems with this method:

*

Headphones do not mute the speakers (which were indeed different channels in other distros)

that's the one part that worries me. 

i use those headphones a lot while i'm in bed at night so i can listen to music. :(

---

### Post by Llewxam on 2008-04-19
out of curiosity, would anyone happen to know if this issue has been resolved in hardy? i do plan to upgrade once the official release is out. much appreciated.

---

### Post by max littlemore on 2008-06-05
Doesn't seem to work on Hardy either.

Very disapointing - on Vista the sound from the mic was crappy, but at least it worked.

Still trying to find a solution....

---

### Post by Llewxam on 2008-06-06
indeed it is. only this and the memory card reader are the only problems i have. so far everything else works great. haven't upgraded to hardy just yet.

---

### Post by sinbadblue on 2008-07-13
omg, it looks like the same issue I have. I just installed ubuntu 8.0.4 because the stupid vista crashed every 20 mins when I am watching HDTV video. Most basic functions are working except the internal mic. my laptop is HP Pavillion dv6736, Conexant CX20561 (Hermosa) which I got from alsamixer. In audio control, there is no "options" tab for internal mic control and no mic items in "capture" tab. Looks like alsa 1.0.6 doesn't support the mic of this chip. sad,sad,sad

I wish this issue will be resolved soon, so that I could completely say goodbye to the stupid vista.

---

