---
title: "Dell 1525 broadcom 4312 wireless Ubuntu 10.10"
date: 2011-12-07
forum: Networking &amp; Wireless
---

### Post by AtomicRobot on 2011-12-07
Can't get it to work. I'm totally new to Ubuntu. I got the wireless to work almost effortlessly the first time I tried it a year ago. Reformatted hard drive, now I can't remember how to get it to work. I activated STA driver. Now I'm trying to figure out what from here. Not familiar with tar or how all that other stuff works. A little help?

---

### Post by chili555 on 2011-12-07
Please open a terminal and run and post:```
lspci -nn | grep 0280
lsmod | grep -e b43 -e wl
dmesg | grep b43
rfkill list all
```This will give us additional details that will help us know how to proceed.

The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

