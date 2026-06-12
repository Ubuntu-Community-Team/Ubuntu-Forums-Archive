---
title: "Intel Vs Jaunty, again..."
date: 2009-09-30
forum: Multimedia Software
---

### Post by nuclear216 on 2009-09-30
I have desktop pc with an old MB with integrated Intel graphics and Celeron 2.4 Ghz, it's a dell Optiplex 170-L desktop.

```
00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)
```


on this particular machine with jaunty neither the driver rollback nor the X-update PPA method restore the graphics performance as they were on the 8.04.

I am downloading the 8.04 LTS version to install on the machine because the graphics in jaunty it's very poor.
I understand that the problem with Jaunty arise because of some changes in the kernel, I wonder if the LTS version receives kernel upgrades that could cripple the performance again, any ideas?

---

### Post by mikewhatever on 2009-09-30
No, it shouldn't. Hardy still has the 2.6.24 kernel version it was released with, as well as the intel graphics driver. The only updates any Ubuntu release receives are security related and major bug fixes.

---

### Post by jperez on 2009-09-30
Well, I think you'll be pleased to know that the alpha of Karmic shows Intel cards working.  I have 3D effects on my laptop again that has an Intel GM965/GL960 Integrated GPU, so Karmic fixes the issue you have.  Jaunty was a very bad upgrade for Intel GPU owners, but Karmic seems to be the cure.  I have a video showing that it works on YouTube.

I waited for a while to see if they would update the driver in Jaunty, but after seeing people say it wouldn't happen, I decided to try Karmic...I'm happy. :D

Jesse~

---

