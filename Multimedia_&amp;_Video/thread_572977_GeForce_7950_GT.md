---
title: "GeForce 7950 GT"
date: 2007-10-11
forum: Multimedia &amp; Video
---

### Post by whiteraven on 2007-10-11
I'm a Ubuntu/Linux noob and dunno exactly why this worked but if it helps someone else...

I've been trying to install the nvidia-glx-new without success - tried every install combo including the restricted drivers manager to utilize the 1600x1200 @ 60Hz I knew the GeForce 7950 GT is capable of displaying.

Without fail, the xserver would fail to start and leave me in text mode. I recalled seeing a thread that recommended simply deleting the /etc/X11/xorg.conf file, which I did figuring another complete OS reinstall wouldn't hurt (I learn something new every time). To my surprise when I rebooted, the display was perfect! 1600x1200 @60Hz.

When I look in /etc/X11 there is no xorg.conf but everything seems to work
Am I missing the boat here? Should I recreate the xorg.conf file? What happens without it?

Thanks in advance!

---

### Post by whiteraven on 2007-10-11
Bump...

I deleted my /etc/X11/xorg.conf, and I confirmed there is no xorg.conf anywhere in my system, but everything seems to work fine - video display, mouse, keyboard and peripherals.

What happens without xorg.conf?
Am I missing the boat here? Should I recreate the xorg.conf file?

---

