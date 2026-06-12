---
title: "Finding drivers for a mobile card"
date: 2010-07-07
forum: Networking &amp; Wireless
---

### Post by erjmfcbat on 2010-07-07
Recently purchased a System76 laptop running Lucid Lynx, new to Linux, wanted to add a mobile broadband card.  My cellular provider supports UM185 - but the product is not documented to work on Linux.  I brought it home anyway, figuring I could find a driver for it.   No luck with any of the searches I have tried.    Looking for guidance on where I should look for drivers, search keywords, OR the name of a supported mobile broadband device/cellular provider.  Thanks

---

### Post by ieee488 on 2010-07-07
I found posts by people claiming that it works out of the box with Ubuntu 9.10

---

### Post by pdc on 2010-07-08
Hi erjmfcbat

if this device is pci, if you copy and paste the results from a terminal of

> lspci

and if you think it is usb, copy and paste

> lsusb

and perhaps what

> dmesg | grep tty (if you copy and paste this last command into a terminal ..)

---

### Post by erjmfcbat on 2010-07-10
[SIZE=2][FONT=Arial]:p  I took a different approach.  Returned the plug in USB device and cancelled mobile broadband service.   Then picked up a Verizon mifi wi-fi hotspot device/service plan.  Cost for device and monthly service equivalent.

The MIFI has to be activated on a Windows system - and the getting started directions will not lead you step by step in spite of the fact they are numbered.  But ...push enough buttons and usually something starts to work......

Once the device is activated(like a cell phone, a one time event), When you turn it on it looks like a wireless network to my laptop.  No problem connecting.  And I believe it supports several (~5) concurrent users.   Wasn't quite ready to dive into terminal windows and drivers, so I am quite happy with this solution.


[/FONT][/SIZE]

---

### Post by pdc on 2010-07-10
enjoy;

these seem very successful devices;

---

### Post by ieee488 on 2010-07-10
> **erjmfcbat said:**
> [SIZE=2][FONT=Arial]:p  I took a different approach.  Returned the plug in USB device and cancelled mobile broadband service.   Then picked up a Verizon mifi wi-fi hotspot device/service plan.  Cost for device and monthly service equivalent.

The MIFI has to be activated on a Windows system - and the getting started directions will not lead you step by step in spite of the fact they are numbered.  But ...push enough buttons and usually something starts to work......

Once the device is activated(like a cell phone, a one time event), When you turn it on it looks like a wireless network to my laptop.  No problem connecting.  And I believe it supports several (~5) concurrent users.   Wasn't quite ready to dive into terminal windows and drivers, so I am quite happy with this solution.


[/FONT][/SIZE]

I have T-mobile mobile broadband for $40/month. Best deal out there that I could find.

---

