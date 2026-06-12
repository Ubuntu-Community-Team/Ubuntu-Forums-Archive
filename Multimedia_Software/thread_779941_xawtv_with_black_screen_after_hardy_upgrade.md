---
title: "xawtv with black screen after hardy upgrade"
date: 2008-05-03
forum: Multimedia Software
---

### Post by ccprog on 2008-05-03
I have a Bt878 video card (Hauppauge). After upgrade to Hardy, xawtv doesn't show the video output any more. The video4linux driver still seems to work, since audio output starts and stops, and I am able to change channels etc. Only the window remains black.

Just to compare things, I installed zapping, and there I get the video (this application has other issues, which is why I can't use it). So to me it seems that the problem really is with xawtv.

My graphics card is a nVidia GeForce4 MX 440, and I use the proprietary driver.

---

### Post by ccprog on 2008-05-03
I found the answer myself. xorg.conf was corrupted and didn't load the i2c module.

---

