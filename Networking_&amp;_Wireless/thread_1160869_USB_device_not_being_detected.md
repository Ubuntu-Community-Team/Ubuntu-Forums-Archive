---
title: "USB device not being detected"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by aknight_sa on 2009-05-16
hello guys,

i have a USB HSDPA modem from Bandluxe, it works as an express card or as a USB adapter.

the issue is i am not able to make it work under Jaunty.

when i do lsusb i get the following output

> 
Bus 001 Device 001: ID ld6b:0002 linux Foundation 2.0 root hub
Bus 006 Device 001: ID ld6b:0001 linux Foundation 1.1 root hub
**[COLOR="Red"]Bus 005 Device 003: ID la8d:1000 [/COLOR]**
Bus 005 Device 001: ID ld6b:0001 linux Foundation 1.1 root hub
Bus 004 Device 001: ID ld6b:0001 linux Foundation 1.1 root hub
Bus 003 Device 001: ID ld6b:0001 linux Foundation 1.1 root hub
Bus 002 Device 001: ID ld6b:0001 linux Foundation 1.1 root hub


the devices is connected and identified in Bus 5 device 3 but its not able to know what it is.

can anyone help me with this?

---

### Post by ddreamer on 2010-08-19
You may try eject it first. If still not working, you may try [http://swiss.ubuntuforums.org/showthread.php?t=886942&page=2](http://swiss.ubuntuforums.org/showthread.php?t=886942&page=2)
My C120 works well with Ubuntu 10.04

---

