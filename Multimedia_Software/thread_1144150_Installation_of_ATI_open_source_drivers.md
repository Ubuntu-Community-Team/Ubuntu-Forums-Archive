---
title: "Installation of ATI open source drivers"
date: 2009-04-30
forum: Multimedia Software
---

### Post by apparle on 2009-04-30
I have found that in 9.04 the fglrx does not support my graphics card..so I am left with no other option but to install open source drivers.

Currently On glxgears, I am getting around 130 FPS in 9.04( fresh install) which is very low as compared to 1300FPS in 8.10 with fglrx...........

So what should I do to obtain reasonable performance from card.......though not as good as from fglrx.

---

### Post by bhaverkamp on 2009-04-30
I would like to know too! I deferred upgrade on one of my notebooks because the installer warned me about the fglrx issue.

---

### Post by Melcar on 2009-04-30
First, glxgears is no indication of performance.  It's more of a test if hardware acceleration is on or not.
Second, the open drivers have on average 1/2 of the raw 3D performance of the proprietary driver (sometimes even worse), so don't expect to get anywhere close to fglrx when it comes to 3D.  However, they have very good 2D performance (better than fglrx in my opinion) and have less of a problem in things like accelerated video playback; the open drivers are even better at accelerating videos under Compiz.
Lastly, if you type "man radeon" on a terminal, you will get a manual of sorts for the driver specifying all the configuration options (to be used on your xorg.conf file).  Try some and see if it changes anything.

---

