---
title: "Atheros usb adapter not working in 9.10"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by AlP36 on 2009-12-04
I have a clean install of Karmic. I am trying to get an EnGenius Long Range USB adapter to work. Right now I am using an Airlink101 Usb adapter. It is slow but it works.
I followed the instructions here:
[http://ubuntuforums.org/showthread.php?t=1307559&highlight=ndiswrapper+install&page=2](http://ubuntuforums.org/showthread.php?t=1307559&highlight=ndiswrapper+install&page=2)

to install the driver for the Engenius and it is installed properly -
alp910@alp910-desktop:~$ ndiswrapper -l
net5523 : driver installed

 and the system says the adapter is present - 
alp910@alp910-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0cf3:0002 Atheros Communications, Inc. AR5523 (no firmware)

However, the adapter does not start (the light is not on and it will not connect). I am wondering if the statement (No Firmware) has significance in the problem. Any help will be appreciated.

---

### Post by mebinte on 2009-12-16
i also have airlink usb adapter. but mines doest work at all, bump

---

### Post by Rampo on 2011-01-10
Same here for me. However I make use of Ubuntu 10.10.

---

