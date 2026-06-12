---
title: "no wlan interface even though modul is registered in kernel"
date: 2010-09-01
forum: Networking &amp; Wireless
---

### Post by Radim on 2010-09-01
Hello,

I am trying to install a wireless LAN USB into Ubuntu 10.04 server edition. Since the WLAN USB module is not supported by the current release I have obtained a Linux driver directly from Realtek.

I have managed to compile and insert the module into kernel - it is listed as 8192cu module (using lsmod command).
However, even though the module is inserted into the kernel, ifconfig or iwconfig does not list any new wireless interface (e.g. wlan0).

Could anyone help me with suggestions how to solve this problem? Thank you.

update: Now I found out that after installing the module, lsusb command does not list the USB device any longer.

---

