---
title: "Bluetooth problems after upgrading"
date: 2012-07-05
forum: Networking &amp; Wireless
---

### Post by redman5087 on 2012-07-05
I've just upgraded from 10.04 to 12.04.
Bluetooth is not working any longer.
It can not not find any devices when searching.

lsusb:

Bus 007 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

hcitool

ubuntu:~$ hcitool dev
Devices:
	hci0	00:0A:94:02:57:19

---

### Post by redman5087 on 2012-07-06
bump

---

### Post by redman5087 on 2012-07-06
Just bought a new  one, everuthing is working now.

As from the new kernels I think they removed support for my old bluetooth stick.

---

