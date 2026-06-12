---
title: "Auto-select 1360x768 at startup (with latest 8.5 drivers)"
date: 2008-06-09
forum: Multimedia Software
---

### Post by barti on 2008-06-09
Just installed Mythbuntu 8.04 on a Gigabyte GA-MA78GM-S2H motherboard (which has the Radeon HD3200 onboard graphics), and it's mostly working fine, save for the fact that it always starts up in 1280 x 1024 resolution. 

The TV it's connected to (via either DSUB or DVI), a Hyundai Q321 LCD seems to report that it's capable of 1360x768, and I can select that resolution once the machine has started (using the Catalyst utility), but is there any way I can force it to select it when GDM starts up?

Stephen

---

### Post by pather on 2008-06-19
do you have it properly writed in xorg.conf?

try this post, some xorg.conf examples are there, also way to make fglrx accept your custom settings.

[http://ubuntuforums.org/showthread.php?p=5221878](http://ubuntuforums.org/showthread.php?p=5221878)

---

### Post by markbuntu on 2008-06-19
Type aticonfig --help in a terminal. It will gve you a list of commands you can use to set up your tv. If the tv is on when the computer is started, it should use what you have configured previously uless it does not recognize it.

What does /var/log/Xorg.0.log say about your tv?

Editing xorg.conf is another method but you must use 

sudo aticonfig --input=/etc/X11/xorg.conf 

after making changes or they will be ignored.

The new 8.6 driver is out. 

It has more tv options in the aticonfig --help

---

