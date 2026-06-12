---
title: "Network Manager auto start"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by shelleycat on 2008-12-20
Kubuntu 8.10, with KDE 4

On boot, network manager does not appear to start.  There is no connection and no indication in the panel.  If I start Network Manager (KNetworkManager is also the menu description), then the wireless connection starts, and the indication appears on the panel.

Is this expected behaviour?

There is a /etc/rc4.d/S28NetworkManager entry, so it should be starting (or is that the wrong run level?)

Laptop ASUS A9Rp, wireless device from lsusb:
Bus 001 Device 003: ID 0b05:171b ASUSTek Computer, Inc. A9T wireless
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  idVendor           0x0b05 ASUSTek Computer, Inc.
  idProduct          0x171b A9T wireless

No wired ethernet present.

---

### Post by shelleycat on 2009-01-03
I have now put a link in ~/.kde/Autostart to knetworkmanager, which seems to give an automatic connection at least some of the time.

---

### Post by joebeasley on 2009-01-03
Default runlevel is 2. 'who -r'

Put it in /etc/rc2.d

---

### Post by shelleycat on 2009-01-05
I've found its (S28NetworkManager) got an entry in runlevel 2 as well.  Sorry, I found the start up file in 4 and never looked any further.

---

