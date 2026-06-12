---
title: "Few questions about the ALSA Driver."
date: 2008-03-14
forum: Multimedia &amp; Video
---

### Post by Ikith on 2008-03-14
Right now I'm using alsa 1.0.14 (Came with ubuntu 7.10 or was upgraded as I installed all of the upgrades). But theres a new version 1.0.16 and I was wondering if I should upgrade to it or stick with 1.0.14? If upgrade then what would be the easiest way to do so?

---

### Post by kpkeerthi on 2008-03-14
If it ain't broke, why fix it? 

Packages in ubuntu, usually, never get updates unless there are critical security fixes upstream. You need to wait 6 months till the next version of ubuntu is released.

However, there is a community maintained [back-ports]("http://packages.ubuntu.com/gutsy-backports/") repository. If you are lucky you may find latest versions of your favorite packages here if someone backports it. You need to enable this repository under System -> Admin -> Software Sources. You may install linux-backports-modules from this repo which contains ALSA 1.0.15 (although it is not going to do any "magic" to your soundcard if it is already working).

If you still need the latest and greatest of ALSA, you are left with compiling it from source. Instructions are [here]("https://help.ubuntu.com/community/SoundTroubleshooting#head-083f68c150e8cc9de635a7ab89b8ccfc6100ecf8"). Its quite simple actually.

---

### Post by Ikith on 2008-03-14
Well thats the thing my sound card PARTIALLY works its a STAC9250. Which suffers the problem of not being able to use the MIC. I was wondering and hoping and praying that upgrading would fix this problem but I haven't heard of it fixing it so I had planned to try it myself.

---

### Post by Bubba64 on 2008-03-14
Personally I always install alsa-oss from synaptic, even though I use alsa, this allows oss to be played by alsa at least that what the program description says.

---

