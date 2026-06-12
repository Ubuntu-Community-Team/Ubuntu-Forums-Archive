---
title: "awl5088 ubnutu 11.04  realtek 8192 usb"
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by mharrall on 2011-05-01
I just upgraded to 11.04  and lost all wifi internal is broadcom bcm43x i have downloaded and install the  driver the driver for the reraltek will not compile due incompatible kernel their drivers available on realteks web site support up to 2.6.32 

but more than that it seems that the wifi is turned of in the os as well and i can not seem to find where to turn it on
unam -a
Linux laptop-boston 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

lspci -vv
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 01)
lsusb -v
lsusb -v
Bus 002 Device 002: ID 0bda:8176 Realtek Semiconductor Corp.
  idVendor           0x0bda Realtek Semiconductor Corp.

modprobe -l
kernel/drivers/net/wireless/b43/b43.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko
kernel/drivers/net/wireless/rtl818x/rtl8180/rtl8180.ko
kernel/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko

thanks in advance for the help

---

### Post by MooPi on 2011-05-01
You may want to roll back to 10.10 if your using the 8192 chip. No love for this on the upgrade. I suggest as others have to contact Realtek for the solution but in the mean time 10.10 is probably best for this model adapter. Have you tried to get the Broadcom chip working instead ?

---

### Post by mharrall on 2011-05-01
that is what i was thinking i have been doing so looking and Debian has a driver working but it is in the unstable tree. Realtek has drivers for up to 2.6.35 kernel. I have emailed Realtek and am awaiting an answer i was just hoping that someone may know something i have not found.
:D

---

