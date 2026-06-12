---
title: "Ubuntu 8.10 - TRENDnet TBW-105UB Bluetooth adapter"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by Kruncher on 2009-04-28
I recently purchased a USB Bluetooth adapter from TRENDnet, model TBW-105UB.

This device works on the Ubuntu 8.04 live cd but not on Ubuntu 8.10.

The Bluetooth manager wont even see the device.

Please someone help get this working.


```
kruncher@kruncher-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```
kruncher@kruncher-desktop:~$ hcitool dev
Devices:
	hci0	00:18:E7:36:D4:7D
```

Thanks,
  Timothy

---

