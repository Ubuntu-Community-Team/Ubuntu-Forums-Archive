---
title: "NETGEAR WG121 woes..."
date: 2006-07-15
forum: Networking &amp; Wireless
---

### Post by matt.sandford on 2006-07-15
Hi all.

I've just installed Ubuntu Linux 6.06 LTS (Dapper Drake) on a laptop of mine.  I have a NETGEAR WG121 54g USB Wireless Adapter connected to one of its USB ports.

On the default 'islsm', 'islsm-usb' drivers that Ubuntu 6.06 comes with, both the USB light and the Wireless light are lit upon boot.  I am able to view 'eth1' in 'ifconfig' and it appears in 'iwconfig' as a device with wireless extensions.

The mode of the device is set to 'Auto' by default, however, when this is the case, I am unable to perform a 'iwlist eth1 scan' or similar command to interact with the wireless adapter.  I then change the mode to 'Managed' with 'iwconfig eth1 mode Managed' and then I am able to perform a 'iwlist eth1 scan' command.

I am able to see the wireless access points that are nearby (including my own), however, i can't seem to connect to it.

Any ideas?

---

