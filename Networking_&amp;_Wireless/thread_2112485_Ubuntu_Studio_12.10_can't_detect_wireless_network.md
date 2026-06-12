---
title: "Ubuntu Studio 12.10 can't detect wireless network"
date: 2013-02-04
forum: Networking &amp; Wireless
---

### Post by IrishSnow35 on 2013-02-04
Hello, I'm referring to my problem in the thread below...forgive my non-use of BBcode, it's been a while since I've been on a forum. [http://ubuntuforums.org/showthread.php?t=1791362](http://ubuntuforums.org/showthread.php?t=1791362)

Anyway, the results of lsusb were as follows...

```
Bus 001 Device 002: ID 111d:0000   Bus 001 Device 003: ID 05ac:8507 Apple, Inc. Built-in iSight Bus 002 Device 002: ID 05ac:8403 Apple, Inc. Internal Memory Card Reader Bus 004 Device 002: ID 05ac:0236 Apple, Inc. Internal Keyboard/Trackpad (ANSI) Bus 004 Device 003: ID 05ac:8242 Apple, Inc. IR Receiver [built-in] Bus 004 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth) Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 004 Device 005: ID 05ac:8213 Apple, Inc.
```
I am working on using the command given to me by chili555, which was as follows, and will reply back once I've gotten those results. Thanks for the help, BTW.
```
lspci -nn | grep 0280
```

---

