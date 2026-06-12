---
title: "YouTube was working fine, now it stutters (other video issues as well)"
date: 2009-06-30
forum: Multimedia Software
---

### Post by juelze on 2009-06-30
Ok, so I went from 9.04 back to 8.10 because of graphics problems.  Someone on this board suggested I try 9.04 again, but stay away from the fglrx driver (I have an ATI 9800pro btw).  Anyway, I did some updates today and it looks like I have some FGLRX stuff that got installed.  Needless to say, now video play back sucks.  It's slow and just horrible.  I really like Ubuntu, but I have a feeling I'm going to have to reinstall 9.04 all over again to get things working like they did before.  However, if I do that, how in the world can I prevent myself from getting that fglrx driver installed again?  

Man, I really like that Ubuntu is pretty rock solid, but it seems that I trade all the errors, viruses, spyware I get with Windows, for software that needs 100 steps just to get one thing to work.  Sorry if I sound frustrated, but 9.04 was treating me right and now I'm having issues.  I want to learn Ubuntu through using it day in and day out but it seems linux holds me back from getting more then a months use before all hades breaks loose. 

Help!!

---

### Post by ssri on 2009-07-01
This guide might help:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

Basically, the last set of instructions will get rid of any interference fglrx is causing:

sudo apt-get remove --purge fglrx*

sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 

sudo apt-get install xserver-xorg-video-ati

sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core

dpkg-reconfigure xserver-xorg

---

### Post by juelze on 2009-07-01
> **ssri said:**
> This guide might help:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

Basically, the last set of instructions will get rid of any interference fglrx is causing:

sudo apt-get remove --purge fglrx*

sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 

sudo apt-get install xserver-xorg-video-ati

sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core

dpkg-reconfigure xserver-xorg

Thank you kindly!!!  I'll try this when I get home and see if it works.  BTW, will this prevent that fglrx driver from downloading in future updates?

Thanks again!

---

