---
title: "WUSB54AG dropping wireless connection"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by dreadnyah on 2009-03-18
I'm using a Linksys WUSB54AG usb wireless interface with a D-Link DSL2640B router. My OS is Ubuntu 8.10, Intrepid Ibex, kernel is 2.6.27-11-generic. The Linksys WUSB54AG uses the Prism54 chipset which is supported in Linux. The driver for the Prism54 is p54.

lsusb output:

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13b1:000c Linksys 
Bus 001 Device 002: ID 054c:0243 Sony Corp. MicroVault Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

dmesg output:
[ 12.397718] firmware: requesting isl3887usb_bare
[ 13.115467] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[ 13.185792] p54: LM86 firmware
[ 13.193421] p54: FW rev 2.5.8.0 - Softmac protocol 3.0
[ 13.637344] p54: unknown eeprom code : 0x1
[ 13.644989] p54: unknown eeprom code : 0x3
[ 13.652588] p54: unknown eeprom code : 0x1908
[ 13.660041] p54: unknown eeprom code : 0x1007
[ 13.667541] p54: unknown eeprom code : 0x1008
[ 13.674823] p54: unknown eeprom code : 0x1100

Notice that the first line of my dmesg excerpt says "firmware: requesting isl3887usb_bare". Checking with the Linux Wireless site ([http://wireless.kernel.org/](http://wireless.kernel.org/)) the file isl3887usb_bare is the correct firmware for my kernel. Why does dmesg report that the kernel was "requesting isl3887usb_bare"? Did it find and load it? Note also that 2 lines down dmesg reports: "p54: LM86 firmware".

Is it using the right firmware?
If not, how do I make it use the right firmware - I can download the firmware file isl3887usb_bare from the wireless Linux site.
If the issue is not be related to the firmware - any ideas as to what it might be?

Regards

dreadnyah

---

### Post by dreadnyah on 2009-03-22
I don't how much interest there is in this problem, considering that the post got no replies and only 28 views.  Clearly the problem is not as widespread as I thought.  

Anyway, for those who may have a similar problem:

I've finally got my wireless network working in intrepid by moving from ubuntu to xubuntu using the identical setup in /etc/network/interfaces and rc.local.  I was using xubuntu before but when upgrading to intrepid I decided to try ubuntu - now I'm back on xubuntu and happy with it especially as it runs so much faster than ubuntu.

---

