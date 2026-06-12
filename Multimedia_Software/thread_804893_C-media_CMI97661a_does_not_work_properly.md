---
title: "C-media CMI97661a does not work properly"
date: 2008-05-23
forum: Multimedia Software
---

### Post by xromano on 2008-05-23
Hi, I found following thread in Archive: [http://ubuntuforums.org/showthread.php?p=5016108#post5016108](http://ubuntuforums.org/showthread.php?p=5016108#post5016108)
There is described solution of problem with CMI6501 which is on board, however must be installed as USB card. I have CMI9761a on board audio, thus I tried the same. However, my card is not in lsusb, but my lspci says something about USB ports for ICH5, which is my audio. Here are lists of lsusb, lspci and alsamixer:
roman@medion:~$ lsusb
Bus 005 Device 003: ID 03f0:6611 Hewlett-Packard
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 004: ID 03f0:3c02 Hewlett-Packard PhotoSmart 7350
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 004: ID 04f2:0200 Chicony Electronics Co., Ltd
Bus 004 Device 005: ID 0bc7:0006 X10 Wireless Technology, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 003: ID 0db0:6982 Micro Star International Medion Flash XL V2.7A Card Reader
Bus 002 Device 001: ID 0000:0000

Well it is obviously nothing concernig sound here. However,
roman@medion:~$ lspci
........
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
......
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
....

This Intel ICH5 I found in alsamixer:
Card: Intel ICH5
Chip: C-Media Electronics CMI9761A

Now I do not understand it. is it possible, that my on-board card is under this ISA bridge? I do not believe it. Could someone check my lists? I would to appreciate it.
Thank a lot for any advice.

---

