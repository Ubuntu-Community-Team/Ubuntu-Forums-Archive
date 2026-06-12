---
title: "relakks pptp wlan 70-persistent-net.rules config"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by cool_vibe_tesla on 2008-12-27
What should I change in below config to get the vpn up in wlan mode?

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x1969:0x2048 (atl2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:23:54:34:94:7b", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x001c (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:22:43:05:b8:90", ATTR{type}=="1", KERNEL=="ath*", NAME="ath0"

---

