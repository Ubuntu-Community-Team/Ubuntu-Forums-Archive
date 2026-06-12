---
title: "Shade of Blue in Youtube Videos"
date: 2012-04-18
forum: Multimedia Software
---

### Post by Crimson Giant on 2012-04-18
I updated Lubuntu this morning, and part of the updates was for my nVidia GeForce driver. Now when I watch Youtube videos there's a shade of blue over them. Is there a setting that I can change to change the colors back to normal? or is it a problem with the video card drivers?

My specs are:

Motherboard: Asus M2N68-AM SE2
Video Card: nVidia GeForce 9600 GT
CPU: AMD Athlon X2 2.93 GHz
Primary Hard Drive: Western Digital 40GB IDE Hard Drive
Secondary HD: Western Digital Caviar Blue 500 GB SATA2 Hard Drive
Optical: LG Standard DVD Drive

---

### Post by ShadowTek on 2012-04-18
I have also been having the same problem, but for several weeks now. It started after an update, but I don't remember which one. It only happens on YouTube, and I'm also using the nVidia proprietary drivers for my GeForce GTS 250.

Found a bug report here:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/976461](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/976461)

---

### Post by haqking on 2012-04-18
right click on the video and choose settings then remove the tick from the enable hardware acceleration so its disabled

Peace

---

### Post by ShadowTek on 2012-04-18
Yeah, I saw that thread further down.

Disabling hardware acceleration didn't have any affect, but downgrading Flash using these instructions solved it:
[http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by Crimson Giant on 2012-04-18
Disabling the hardware acceleration worked; it's back to normal again. Thanks guys! :D

---

### Post by haqking on 2012-04-18
> **Crimson Giant said:**
> Disabling the hardware acceleration worked; it's back to normal again. Thanks guys! :D

you are welcome.

remember to use thread tools to mark the thread as solved to aid others in the search for similar issue.

peace

---

