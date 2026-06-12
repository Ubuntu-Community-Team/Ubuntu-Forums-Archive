---
title: "Upgrade to 11.10, wlan0 missing"
date: 2011-11-05
forum: Networking &amp; Wireless
---

### Post by whein on 2011-11-05
I just upgraded from 11.04 to 11.10 last night.  Prior to the upgrade my wireless connection was working fine.

After the reboot after the upgrade, wlan0 seems to have vanished and I don't know how to get it back.

running "nm-tool" only shows eth0 (which isn't connected to anything)
running "lspci" shows my wireless card correctly
[INDENT]03.07.0 Network controller: Ralink corp. RT2800 802.11n PCI[/INDENT]
running "sudo iwconfig" shows only lo and eth0 but not wlan0

All the help pages and threads I've found so far assume wlan0 shows up in iwconfig (which it used to before the upgrade) but I don't know how to fix it if it doesn't!

running "sudo lshw -C network" does show the wireless card but it lists it as unclaimed and doesn't show a driver for it.

help?  please?  I'll send cookies?

-Will

---

### Post by jawilljr on 2011-11-05
Try this:

```
sudo modprobe rt2800pci
```

Jerry

---

