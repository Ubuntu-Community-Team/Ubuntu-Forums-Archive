---
title: "Mobile USB Modem- How to setup"
date: 2011-07-27
forum: Networking &amp; Wireless
---

### Post by raunhar on 2011-07-27
I recently purchased a Spice 3G phone, which can also be used as a Modem.

When I plug it into the USB, the phone starts charging.But when I go to Edit Connections--> Mobile Broadband, I cannot see the MODEM there. The Select the device is not highlighted.

LSUSB command shows:
Bus 002 Device 007; ID d324;9003

How do I make it detect so that I can use the phone as Modem.

---

### Post by Mcjohnnson on 2011-07-27
It is working with my samsung galaxy 5 (GT-I5500) right out of the box.
See [here]("http://dickmcjohnnson.blogspot.com/2011/07/usb-tethering-with-android-21-handset.html")!

lsusb is giving me back:
```
Bus 002 Device 004: ID 04e8:689e Samsung Electronics Co., Ltd 
```

---

