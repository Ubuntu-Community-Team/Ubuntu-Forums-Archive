---
title: "xbmc and nouveau"
date: 2014-10-09
forum: Multimedia Software
---

### Post by danielsender on 2014-10-09
I'm running 14.04.1 on a M70 Dell laptop that has the Quadro4 500 GoGL. Apparently Ubuntu doesn't package the NVIDIA proprietary driver (96x) anymore so clicking on "Additional Drivers" doesn't show anything available. So I'm pretty much forced to use nouveau and Gnome flashback (metacity) as the manager. Everything is OK, however XBMC does not work. I posted the issue on the XBMC website and they told me that with nouveau it always segfaults. So my question is if anybody got XBMC to work with the nouveau driver and if so, what did they do to get it to work.

Many thanks in advance.

Daniel

---

### Post by danielsender on 2014-10-10
bump

P.S. made a mistake: is not an M70 but an M50.

---

### Post by sp40140 on 2014-10-13
I run GeForce 210 on Core2Duo desktop ubuntu 14.04.01, latest stable xbmc - Gotham. on open source drivers. didn't have to do anything. just worked. But I have tried the prop drivers from the "additional drivers" menu and it has worked for me in the past as well.
What does the error dump from xbmc say? Also, have you checked /var/log for errors? what do they say?

---

### Post by danielsender on 2014-10-13
For this old hardware (NVIDIA NV17GL [Quadro4 500 GoGL]), clicking on "Additional Drivers" does not result in any proprietary drivers (e.g. 96.43.x), so the only usable driver is the Nouveau which does not seem to work together with XBMC.

---

### Post by Rob Sayer on 2014-10-14
Read this carefully:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by danielsender on 2014-10-14
I did, the response to typing "sudo ubuntu-drivers devices" is nothing - same thing as from the GUI.

---

### Post by Rob Sayer on 2014-10-14
I suspect the nvidia driver that used to work doesn't work anymore with the current kernel, and that's been true for some time.

---

### Post by danielsender on 2014-10-14
I think that is exactly the problem, I'm just wondering what is the development status of the nouveau drivers, when will they get to have working acceleration.

---

### Post by khPWXxF on 2014-10-15
Nvidia tool a step back wards with 14.04.  Go over to mythbuntu forum look for a thread by paul164 about 4 weeks ago "14.04.10 a disaster"
Sorry I can't paste the link with this  device
Phil

---

### Post by Rob Sayer on 2014-10-15
My usual response to this sort of thing is "don't hold your breath".  Intel is good at updating drivers with hardware support issues is better than any others I know, but my netbook has the intel (but they outsourced it) cedarview GMA3600 video.  It doesn't have proper 3D accel and I don't think it ever will.

I'd start trying other media programs myself, especially if there's nothing useful at the xmbc forums.

---

### Post by danielsender on 2014-10-15
Nouveau started almost ten (10) years ago in 2005 by Mr. Marchesin and followed by many folks later - I wonder how much longer would take to get full acceleration working properly.

---

