---
title: "MAC address changes on each restart"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by Phil Usher on 2009-05-31
Hi Gang,

Having a problem with my wired connection with 9.04 (jaunty).   On each reboot the MAC address for my wired connection changes.  This causes my DHCP server to allocate a new IP address.

/etc/udev/rules.d/70-persistent-net.rules
```
# PCI device 0x10de:0x0269 (forcedeth)
SUBSYSTEM=="net", DRIVERS=="forcedeath", NAME="eth0"

# PCI device 0x10de:0x0269 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:6c:e1:04:0d", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
```Note the second line.  Each reboot will produce a new entry.

Any help appreciated.

Cheers ... Phil Usher

---

### Post by Iowan on 2009-05-31
Have you tried commenting out the second line and making the last line end with NAME="eth0"? (Or leave it as eth1 to see if it is at least stable)

---

### Post by Phil Usher on 2009-05-31
Thanks for the suggestion.  Removing the second and leaving the first line produced the code seen above.  So I commented out the first line leaving the second - rebooted and the problem persists here is the resultant 70-persistent-net.rules file.

```
# PCI device 0x10de:0x0269 (forcedeth)
# SUBSYSTEM=="net", DRIVERS=="forcedeath", NAME="eth0"

# PCI device 0x10de:0x0269 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:6c:e1:04:0d", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10de:0x0269 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:6c:7f:d5:fb", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
```

---

