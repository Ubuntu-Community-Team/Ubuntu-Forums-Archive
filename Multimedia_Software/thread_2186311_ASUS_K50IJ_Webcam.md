---
title: "ASUS K50IJ Webcam"
date: 2013-11-06
forum: Multimedia Software
---

### Post by akarawx on 2013-11-06
I've looked at other guides, many other posts and have tired many things, yet none work. I'm trying to get my webcam working on x64 Ubuntu 13.10.

lsusb:
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




I can't quite figure out what to do, I've tried updating, and I've tried many different guides and posts to get my webcam working but so far nothing does the job, Cheese doesn't show nor skype. VLC has no output but says my camera is there .-. Help please?

---

### Post by akarawx on 2013-11-08
Fixed on my own, turns out that 13.10 didn't compile the drivers right? o.O anyway just removed the old drivers and installed new ones restarted and now it works :)

---

