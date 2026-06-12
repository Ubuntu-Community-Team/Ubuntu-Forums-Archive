---
title: "Hardware Driver List"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by wwjdd44 on 2010-06-25
I am using a Dlink DWA 130 usb network adapter.  It uses the realtek 8192su chipset.  I downloaded the latest linux driver from Realtek.  The driver seems to install okay, but I have no network connection and no evidence of wlan0.  If I look in the Hardware Driver list, is shows up there as being active, but not in use.  If I deactivate the driver, then reactivate it, it works fine.....giving the N speeds I am looking for.  But when I shut the computer down and restart it, I have to go through the same process to get it activated and in use again.  Anyone have an idea on how I can get this to work without having to go through this process when I turn on the computer ??


I solved my own problem.  I do not know why or how, but by putting the line "modprobe 8712u" into the /etc/rc.local file, the adapter initializes upon being rebooted.

---

