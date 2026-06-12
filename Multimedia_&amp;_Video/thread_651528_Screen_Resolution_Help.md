---
title: "Screen Resolution Help"
date: 2007-12-27
forum: Multimedia &amp; Video
---

### Post by carnivalxx on 2007-12-27
So I recently switched from just XP to a dual boot of XP and Ubuntu using Wubi. :D

In XP, I could increase my screen resolution to 1280 x 1024. But when I boot Ubuntu, I cannot increase my resolution beyond 640 x 480. 

What would I have to do in order to increase my screen resolution? As with that small of a resolution, I cannot view certain webpages, or even some of the dialog boxes Ubuntu asks me to fill out in the System Preferences, but I think you get my point of this small resolution limiting my ability to operate my computer properly.

Any help at all would be greatly appreciated. :)

---

### Post by Zalbor on 2007-12-27
What kind of graphics card are you using? Didn't the restricted drivers manager appear after you installed? It's probably a case of installing the proper drivers.

---

### Post by moron on 2007-12-27
Sounds like you will need to mess around with your Xorg configuration.  This will require knowing details about your monitor, video card and current Xorg configuration.  I would start by noting what video card you have, what monitor you have and your current /etc/X11/xorg.conf file contents.

Cheers

---

### Post by carnivalxx on 2007-12-28
My graphics card is an Intel® 82845G Graphics Controller and I just have a big black Dell monitor and I have no idea what the Xorg configuration is. :P

The restricted driver manager may have appeared, I didn't really pay attention. :(

How would I install my driver? :confused:

Thanks for the help everyone. :D

---

### Post by carnivalxx on 2008-01-01
Sorry to double post, but I looked into the restricted driver manager on my system, and got this error:
> You need to install the package

  linux-restricted-modules-2.6.20-16-generic

for this program to work.

How would I fix this now?

Thanks for any help, it is greatly appreciated. :)

---

