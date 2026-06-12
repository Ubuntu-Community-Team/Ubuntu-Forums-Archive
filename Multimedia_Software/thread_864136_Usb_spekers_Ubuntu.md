---
title: "Usb spekers Ubuntu"
date: 2008-07-19
forum: Multimedia Software
---

### Post by sigma_50 on 2008-07-19
How do i get my USB audio speakers to work in Ubuntu 8.04 with KDE 3.5x with kernel 2.6.24-16

lspci |grep audio
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)

lsusb
Bus 002 Device 005: ID 0d8c:0103 C-Media Electronics, Inc. Turtle Beach Audio Advantage Micro

i put this line in the /etc/mplayer/mplayer.conf
ao=alsa:noblock:device=hw=1.0
and that made the usb speakers work in Mplayer, but nowhere else, how do enable usb speakers everywhere in Ubuntu. Thanks in advance.

---

