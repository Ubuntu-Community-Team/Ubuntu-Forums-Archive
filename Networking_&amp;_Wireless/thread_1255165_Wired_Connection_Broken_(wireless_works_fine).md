---
title: "Wired Connection Broken (wireless works fine)"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by matski on 2009-09-01
Hi.  After the latest round of updates my wired connection has stopped working.

eth0 is configured with a public IP
eth0:1 is configured with a private IP

Removed the static entries and replaced with a DHCP address.  Picks one up fine but still unable to find route to network on anything outside of the lan.

Plugged a usb wireless dongle in and it picked up a DHCP address from the same subnet as assigned to the lan interface.  This works fine, I can get outside of the lan straightaway.

Anyone help?  Let me know what other info/outputs you want? Cheers, Mat

---

### Post by matski on 2009-09-01
Tracked down a similar issue and tried disabling NetworkManager and using the interfaces config file instead.  This was a fail for both dhcp and static assignment :(

---

### Post by matski on 2009-09-01
Solved it.

Stuck a pci network card in and works fine with dhcp and static addressing.

For info, the onboard controller is a HP RTL8111/8168B Gigabit jobby.

---

