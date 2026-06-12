---
title: "Ubuntu / Debian drivers interchangable?"
date: 2008-08-16
forum: Multimedia Software
---

### Post by Cool Javelin on 2008-08-16
Hello good Ubuntu Users and Gurus:

I have a triple boot system with Ubuntu Hardy, Debian Etch, and win98.

In Ubuntu, it hasn't installed the proper driver for the Via Tech VT8361/VT8601 and I am limited to 800x600.

Debian has installed the proper driver and the video works fine and I am able to select a very high resolution.

I have separate partitions for the 2 distros (they share a swap partition only.)

There is a similar problem in reverse for my sound card. Ubuntu has sound OK, but the Debian install dropped the ball. When clicking on the little speaker (there is a little x in the icon,) it complains there is no sound device found.

#1, Where are the drivers located in the distros, and how are they loaded at startup (is this done in X, or outside in Linux proper?

#2, since Ubuntu and Debian are so close, can I use the Debian video driver in Ubuntu and vice versa?

Thanks for your help,
Mark.

---

### Post by wolfen69 on 2008-08-16
in ubuntu, try this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then reboot or restart x.

---

### Post by Cool Javelin on 2008-08-20
Thanks wolfen69:

I did try your suggestion, but it didn't seem to have any effect. What is it supposed to do?

---

