---
title: "Bluetooth not working if not switched off in windows first"
date: 2011-06-16
forum: Networking &amp; Wireless
---

### Post by gambiting on 2011-06-16
Hi there! I'm running ubuntu 11.04 x64 2.6.38-8, and I don't know the exact model of my bluetooth card, it just shows up as Bluetooth 2.1+EDR, I can't find it using lspci or lsusb. The laptop is MSI GT640.

The problem is that if I run Windows, and leave the bluetooth working, then in ubuntu the scanning won't work. I can still switch the device on or off, but I can't see it from outside even if it is set to visible mode, and neither can I scan for other devices. However, when I turn the bluetooth off in Windows, and then reboot into ubuntu, everything works perfectly,I can scan and connect to other devices just fine. I guess it's because windows puts it into some kind of sleep mode, from which ubuntu never wakes it up, despite loading the correct module, and switching the device off and on.

Could somebody help me please?

---

