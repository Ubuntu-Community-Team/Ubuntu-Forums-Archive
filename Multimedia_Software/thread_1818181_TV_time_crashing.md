---
title: "TV time crashing"
date: 2011-08-04
forum: Multimedia Software
---

### Post by ukmad on 2011-08-04
I have ubuntu 10.04 and was using TYV TV viwer for over 2 years but yesterday sudenly it stopped working
when i click the icon nothing happens window opens and shuts
I tired this :
sudo tail -f /var/log/messages
Result: 

Aug  4 20:24:00 uday-desktop kernel: [  531.669039] tvtime[1482]: segfault at 6b0 ip 0804d824 sp bfd4b56c error 4 in tvtime[8048000+76000]
Aug  4 20:24:19 uday-desktop kernel: [  550.795207] lo: Disabled Privacy Extensions
Aug  4 20:35:18 uday-desktop kernel: [ 1209.038613] lo: Disabled Privacy Extensions
Aug  4 20:44:37 uday-desktop kernel: [ 1768.987601] lo: Disabled Privacy Extensions
Aug  4 20:45:11 uday-desktop kernel: [ 1802.787718] Linux video capture interface: v2.00
Aug  4 20:45:11 uday-desktop kernel: [ 1802.820870] saa7130/34: v4l2 driver version 0.2.15 loaded
Aug  4 20:45:11 uday-desktop kernel: [ 1802.829222] saa7134 ALSA driver for DMA sound loaded
Aug  4 20:45:11 uday-desktop kernel: [ 1802.829229] saa7134 ALSA: no saa7134 cards found
Aug  4 20:48:27 uday-desktop kernel: [ 1998.898446] tvtime[1889]: segfault at 6b0 ip 0804d824 sp bf9efc9c error 4 in tvtime[8048000+76000]
Aug  4 20:55:52 uday-desktop kernel: [ 2443.472130] tvtime[2092]: segfault at 6b0 ip 0804d824 sp bf8ac3ec error 4 in tvtime[8048000+76000]


can u help in this,.

Have KDE TV insatlled as well but cant configure that

---

