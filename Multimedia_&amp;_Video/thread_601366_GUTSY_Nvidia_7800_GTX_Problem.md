---
title: "GUTSY Nvidia 7800 GTX Problem"
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by bonka on 2007-11-03
Hey,

When I boot up the live cd for the new ubuntu, it gives me a funny picture on screen. As I am using two screens, the left screen has the first 2 inches of the screen moved over to the right of the screen and is on top of the new two inches. Some of the lines on screen are also visibly just some straight white lines. The second screen just has green and white colours all over the place.

I had used it in safe graphics mode and it works fine. From that I know it is the graphics drivers as also ubuntu will not let me enable the drivers after installing ubuntu in safe graphics mode.

I hope someone can help me with this problem, you might have to bear with some noob type questions.

Thanks,

Bonka

---

### Post by drummingpariah on 2007-11-09
Try googling "envy" as it seems like newer drivers would really help you.  Envy is a great little suite that installs the latest drivers for you, saving all the hassles.  After that, let us know what version of the drivers was installed and if you're still having problems.

---

### Post by eye208 on 2007-11-09
> **bonka said:**
> When I boot up the live cd for the new ubuntu, it gives me a funny picture on screen. As I am using two screens, the left screen has the first 2 inches of the screen moved over to the right of the screen and is on top of the new two inches. Some of the lines on screen are also visibly just some straight white lines. The second screen just has green and white colours all over the place.
I experienced similar display corruption while booting the Live CD of Gutsy and earlier versions as well. I suppose it is caused by the automatic video card detection procedure which is executed only during Live CD startup. It never occured with the installed system. IMHO it is nothing to worry about.

> From that I know it is the graphics drivers as also ubuntu will not let me enable the drivers after installing ubuntu in safe graphics mode.
Installing Ubuntu in safe graphics mode will make X.org use the "vesa" driver. You can switch to a different driver at any time later. The recommended method to enable the Nvidia binary driver is by using the Restricted Drivers Manager from the Administration menu (Ubuntu) or the KDE system settings panel (Kubuntu).

---

