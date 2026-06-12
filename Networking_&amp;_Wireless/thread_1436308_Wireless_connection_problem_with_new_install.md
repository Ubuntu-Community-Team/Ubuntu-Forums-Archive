---
title: "Wireless connection problem with new install"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by ecomar on 2010-03-22
So I just installed Ubuntu 9.10 and it is not recognizing my wirless device. I have a Broadcom corporation BCM4311 802.11b/g WLAN card. Does anyone know how I should proceed to get this darn internet workin?

---

### Post by bkratz on 2010-03-22
> **ecomar said:**
> So I just installed Ubuntu 9.10 and it is not recognizing my wirless device. I have a Broadcom corporation BCM4311 802.11b/g WLAN card. Does anyone know how I should proceed to get this darn internet workin?

The driver b43 appears to support this device now, see the following

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

Look at the section labeled  "Ubuntu/Debian"

---

### Post by TBABill on 2010-03-22
I had the same problem with my Broadcom. If you can, plug into your router and update your system. It may just prompt you to install the proprietary driver. If not, go to hardware (under "settings"?) and have the system scan for devices needing a proprietary driver. For me, the Broadcom driver came up and I selected it, rebooted (and disconnected the hardwire to the router) and then connected to my router.
 
It's a pain, but easy enough to do if you can get the computer to the router one time.

---

