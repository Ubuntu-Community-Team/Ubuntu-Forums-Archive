---
title: "Networking Problems With USB Device"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by Steelfan555 on 2009-01-01
(using 8.1) I used Ndiswrapper and the GUI Version. I then Got the drivers for my WUSB54GSC v2. I read about an issue and then added usb8023.sys and rndismp.sys to the driver file ( /etc/ndiswrapper/wusb54gsc ) I then checked back to see if it worked using System>Administration>Windows Wireless devices. The Hardware is present and the driver does work. So when i tried to get into my wpa network, it doesn't work. I looked into it and it replaced my password with random garble (8d9342b1580d5827..., it was like 50 digits:(  ) I tried to change it, but it always returns to the garble. Any ideas would be greatly appreciated, thanks in advance.
~Steel

---

### Post by Noel96 on 2009-01-02
Is a wireless network detected?

Have you tried disabling the WPA network password in your modem and seeing if that works? 

Recently I installed a USB wireless device and it worked fine when the WPA was disabled. The minute I tried to set a WPA, though, it wouldn't connect.

---

