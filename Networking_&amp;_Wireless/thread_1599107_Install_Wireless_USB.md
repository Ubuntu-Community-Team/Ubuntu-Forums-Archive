---
title: "Install Wireless USB"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by windbornej38 on 2010-10-17
Hi, i'm a newbie, and i just installed Ubuntu Christian Edition in place of Windows Vista. i would like to use the Airlink 300N USB Wireless Adapter which was not detected by U OS. i'd appreciate information as to how to install a driver for this device.

---

### Post by chili555 on 2010-10-17
Please open Applications > Accessories > Terminal and type in:```
lsusb
```Is this your device?> Bus 001 Device 004: ID 0bda:8174 Realtek Semiconductor Corp. If so, it is supposed to work with the module *r8192s_usb* which is built in to the latest version, but, evidently, not the Christian edition which is based on version 9.10.

Do you have the driver disk that came with the USB device?

Please post the results of the *lsusb* command and we'll be glad to help you.

---

