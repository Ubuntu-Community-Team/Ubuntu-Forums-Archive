---
title: "Wireless card works, but is someimes wlan0 and other times wlan1"
date: 2012-03-18
forum: Networking &amp; Wireless
---

### Post by dragonfriend0013 on 2012-03-18
I have a Linksys WMP54G rev 1 card installed on my Ubuntu 11.10 rig.  This card works perfectly, however sometimes it is recognized as wlan0 and other times (after reboot) as wlan1.  What is causing this behavior?  Internet still works, this is just messing up my Conky setup.

---

### Post by dragonfriend0013 on 2012-03-20
Figured it out.  I went from having a USB wireless dongle to the PCI card.  udev still had the USB dongle listed, so sometimes the wlan assignment would get hosed up.  By deleting /etc/udev/rules.d/70-persistent-net.rules and restarting, all has been taken care of.  This file now looks like:

```
# PCI device 0x11ab:0x4362 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:01:29:a4:78:13", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:0x0201 (rt2500pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:12:17:99:71:7a", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
```

---

