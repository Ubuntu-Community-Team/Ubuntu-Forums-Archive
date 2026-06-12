---
title: "Built-in webcam doesn't work"
date: 2010-01-31
forum: Multimedia Software
---

### Post by myMindsAvatar on 2010-01-31
Hi all,

Linux newbie here. I've just made the big jump into the free world and it's mostly been a wonderfully liberating experience (Ubuntu 9.10). I've run into a couple of sticky patches, which from what I've read is related to my laptop (Acer Aspire 6920, ATI graphics,etc), but I want to start using my built-in / integrated webcam... trouble is, it doesn't seem to work. Everything I've tried can't seem to find it (e.g. Cheese, StopMotion (my real motivation)).

I've looked around but haven't found much help for the real newbie, so this should be relatively easy to resolve...famous last words. 

(See below) I think I've established there's a webcam there (Chicony Electronics Co., Ltd), and this uses the uvcvideo driver... now what?

Many thanks
Richard ~

Here's a terminal copy:
richard@richard-laptop:~$ lsusb
Bus 002 Device 003: ID 04f2:b044 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 138a:0001 DigitalPersona, Inc Fingeprint Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
richard@richard-laptop:~$ dmesg | grep 04f2:b044
[    6.093186] uvcvideo: Found UVC 1.00 device CNF7017 (04f2:b044)

---

