---
title: "Want to try NVIDIA accelerated graphic driver and have fall back option"
date: 2011-04-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Yumi on 2011-04-14
The system suggests to activate the NVIDIA accelerated graphics driver. Last time I did this the system came to a halt and I could not revert (deactivate) but had to reinstall.

Before I try again, how can I go back to the present state?

Michael

---

### Post by iiiears on 2011-04-14
I would reboot and use the safe mode to use VGA. if things went badly and then synaptic to remove install what you want.

If there is an xorg.conf in /etc/X11 make a backup first. Was it created on install?
nvidia-xconfig or dpkg-reconfigure xserver-xorg -phigh or 
aticonfig --initial no idea what intel chip drivers need.

---

### Post by dino99 on 2011-04-14
dont use outdated/third party commands as kernel now directly deal with drivers, they only bring & push mess

sudo rm /etc/X11/xorg.conf

---

