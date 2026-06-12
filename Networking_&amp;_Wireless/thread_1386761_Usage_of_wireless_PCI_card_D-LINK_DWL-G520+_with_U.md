---
title: "Usage of wireless PCI card D-LINK DWL-G520+ with Ubuntu 9.10"
date: 2010-01-21
forum: Networking &amp; Wireless
---

### Post by mbeccaria on 2010-01-21
This wifi card is not recognised by the system; ifconfig does not return any wlan0 interface
I have googled and understood that the card is based on Texas Instrument chipset ACX111. Apparently the driver for it is no more part of Ubuntu 9.10
I have downloaded the sources, compiled them after the installation of a patch.
Loaded the driver with insmod command.
The driver starts but claims no firmware file is found.
Then I have followed the steps below
- copied any of the firmware files (like ti****) available under /lib/firmware/acx/.... under the /lib/firmware folder, that should be the firmware hotplug directory
- reboot of the PC
- insmod acs.ko

then the PC stops working, and the keyboard leds start blinking (kernel panic ???)

Anybody can help ??

P.S: someone suggested to use the native Win driver under ndiswrapper, but I have no experience with it...

---

