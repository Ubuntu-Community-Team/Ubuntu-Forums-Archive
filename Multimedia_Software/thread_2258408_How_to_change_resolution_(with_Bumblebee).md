---
title: "How to change resolution (with Bumblebee)?"
date: 2014-12-27
forum: Multimedia Software
---

### Post by bm1648 on 2014-12-27
[TABLE]
[TR]
[TD="class: votecell"]     1     down vote          [favorite]("http://askubuntu.com/questions/565597/how-to-change-resolution-with-bumblebee#")[/TD]
[TD="class: postcell"]                I need to change the screen resolution on my Lenovo g500s (Intel HD Graphics + NVIDIA® GeForce GT720 M) notebook, unfortunately,  xrandr only shows something like that. I'm using Bumblebee. By nvidia-settings doesn't work.

  xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1366 x 768, current 1368 x 768, maximum 1368 x 768
default connected primary 1368x768+0+0 0mm x 0mm
1366x768 0.0
1368x768 0.0* 

sudo lshw -c display
*-display UNCLAIMED
description: VGA compatible controller
product: 3rd Gen Core processor Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 09
width: 64 bits
clock: 33MHz
capabilities: msi pm vga_controller cap_list
configuration: latency=0
resources: memory:d3000000-d33fffff memory:e0000000-efffffff ioport:4000(size=64)

  How to change resolution?

  Ubuntu 13.10 Lenovo g500s Intel Pentium 2020M 2.4 GHz Intel HD Graphics (Ivy Bridge), 350-1100 MHz, 9.17.10.2963 + NVIDIA® GeForce GT720 M 4096 MB , DDR3, Single-Channel Screen 15.6 16:9, 1366x768, Samsung L ATLTN156AT30L01, TN,[/TD]
[/TR]
[/TABLE]

---

### Post by overdrank on 2014-12-27
Hi and welcome, Ubuntu 13.10 is no longer supported. Best to update the system. :)

---

### Post by bm1648 on 2014-12-27
Will it change anything about my problem?

---

