---
title: "New nvidia-glx, kernel loads old module"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by fuag155555 on 2007-06-29
Hello, I'm on kubuntu 7.04 fiesty amd64 branch, with the recent change from the 87** drivers to the 96** nvidi drivers, after a reboot, x will no longer start because it says the nvidia-kernel modules is 1.0.76** and my driver module is 96**.

However if i do a sudo rmmod nvidia, then sudo modprobe nvidia, the correct 96** kernel module is loaded and i can then run startx and continue normally.

I've tried making a new initramfs image, tried listing nvidia on the blaclist then putting it in /etc/modules, and i have tried disabling nvidia in /etc/default/linux-restricted-modules-generic, all to no avail, somehow the old kernel module always gets loaded. I have also tried using module assistant to force a recompile and install of the 96** driver to no avail. My package names are

ii  nvidia-glx                      1.0.9631+2.6.20.5-16.29        NVIDIA binary XFree86 4.x/X.Org driver
ii  nvidia-kernel-2.6.20-16-generic 1.0.9631-0ubuntu3+2.6.20-16.29 NVIDIA binary kernel module for Linux 2.6.20
ii  nvidia-kernel-common            20051028+1ubuntu7              NVIDIA binary kernel module common files
ii  nvidia-kernel-source            1.0.9631+2.6.20.5-16.29        NVIDIA binary kernel module source

I've pokedc around on the irc channels but no-one seems to know whats going on. Thanks for reading

I've made a workaround by making a local init script that does

rmmod nvidia
modprobe nvidia

but i would really apreciate getting back to the normal way for ubuntu, what package should i file the bug report under?

-Mike

---

