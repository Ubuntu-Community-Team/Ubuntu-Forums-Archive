---
title: "Wireless Broadband No Longer Works"
date: 2010-06-28
forum: Networking &amp; Wireless
---

### Post by ..::| Dave89 |::.. on 2010-06-28
I have a Huawei E160E Mobile Broadband USB modem, which works fine with my desktop PC running 64-bit Lucid, and used to run well with my laptop when running 32-bit Karmic, but since upgrading it to 64-bit Lucid, I can't get it to run, using the same steps as described in the thread linked to below, which is exactly how I got it to work with the desktop. I've tried reinstalling Ubuntu without success, any sugestions?  I'll downgrade back to Karmic if I have to, haven't got my original 32-bit ISO anymore, but have a 64-bit one on a magazine cover disc.



[http://ubuntuforums.org/showthread.php?t=1014221](http://ubuntuforums.org/showthread.php?t=1014221)

---

### Post by ..::| Dave89 |::.. on 2010-06-28
I tried the workarounds mentioned in [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475) nothing.  I downloaded Linux Mint 9, not really expecting it to work, but got it connected no problem on the liveCD, so I'm installing it now.  I'll still keep Ubuntu installed on my desktop though.

EDIT: Once installed it doesn't work, same as in Ubuntu.  Strange it works on the liveCD, but not on a proper install.  I've installed usb-modeswitch


EDIT # 2: Don't know if this helps:

```

dave89@dave89-laptop ~ $ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

dave89@dave89-laptop ~ $ dmesg | grep tty
[    0.000000] console [tty0] enabled

```

---

