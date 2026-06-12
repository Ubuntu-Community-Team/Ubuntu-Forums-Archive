---
title: "DViCO Fusion 4 HDTV DVB-T Gutsy Gibbon"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by dananimal on 2007-10-29
I'm trying to get my DVB-T card working again 
(I had it operating fine under feisty and it worked for a while on Gutsy but then...it just stopped)

I previously had it working using this howto:
[http://fremnet.net/article/228/dvico-fusionhdtv-dual-digital-4-under-linux]("http://fremnet.net/article/228/dvico-fusionhdtv-dual-digital-4-under-linux")

And it worked fine for ages, until shortly after I installed Gutsy.

There is a recommendation here:
[http://www.mythtv.org/wiki/index.php/DViCO_FusionHDTV_DVB-T_Dual_Digital_4]("http://www.mythtv.org/wiki/index.php/DViCO_FusionHDTV_DVB-T_Dual_Digital_4")
to downgrade to an earlier version of the V4L DVB drivers, but I don't know how to get the earlier snapshot.

Does someone know the magic text to grab this code?

---

### Post by oobe-feisty on 2007-11-15
hey i have the exact same card if your still having trouble i wrote 2  tiny shell scripts

i made a tarball just ./dvb_installer

an after thought these files i made are based on the first link you gave and if this does not work for you im thinking that it may be your kernel version im running a vanilla kernel 2.6.23.1 i once remember compiling from the newest linuxtv source tree and getting errors cause my kernel wasnt 
new enough so if these files i posted dont work then you can try compiling a vanilla kernel its not that hard just a bit time consuming google ubuntu kernel compile and you will find loads of instructions that automate the process

P.S the first script dvb_installer copys the second script to /usr/bin it removes the modules and reloads them if you ever need to do this again just type" sudo dvb-reload "

---

