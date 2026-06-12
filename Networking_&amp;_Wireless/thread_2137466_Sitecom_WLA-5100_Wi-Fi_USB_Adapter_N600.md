---
title: "Sitecom WLA-5100 Wi-Fi USB Adapter N600"
date: 2013-04-20
forum: Networking &amp; Wireless
---

### Post by geus on 2013-04-20
Hi,

Anyone that could tell me if it' s at all possible to get a Sitecom WLA-5100 Wi-Fi USB Adapter N600 working in (L)ubuntu?
Some info that might be relevant:

lsusb
Bus 002 Device 006: ID 0df6:006f Sitecom Europe B.V. 

dmeg 
[ 4150.176018] usb 2-2: new high-speed USB device number 7 using ehci_hcd
[ 4150.323967] usb 2-2: New USB device found, idVendor=0df6, idProduct=006f
[ 4150.323972] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 4150.323975] usb 2-2: Product: 802.11 n WLAN
[ 4150.323978] usb 2-2: Manufacturer: Ralink
[ 4150.323980] usb 2-2: SerialNumber: 1.0

iwconfig shows only lo and eth0

uname -r
3.5.0-27-generic

I can't even tell the ralink chipset number from lsusb.

Tried modprobing rt2x00usb and rt2800usb to no avail, but suspect the USB ID isn't listed in those drivers as of yet.
I suspect this USB stick isn't supported in the kernel I have. Anyone that could confirm/deny this assumption, and if correct,  could shed some light as to if it will be supported in the (near) future?

Installed linux-backports-modules-cw-3.6-quantal-generic but doesn't do much up till now.
Much appreciated and kind regards,

Geus

---

### Post by JHyWMPG on 2013-10-11
up. 
same problem, is there someone who can help me? 
i have the sitecome wla-5100 pen but i can't connect to wifi...

---

### Post by JHyWMPG on 2013-10-14
up

---

