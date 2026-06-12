---
title: "Wifi being assigned eth* not wlan*"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by schizostatic on 2009-04-23
So I searched the forums and google and so far everything I found didn't help me. Here is the problem. My wifi instead of being identified as wlan0 is assigned to eth1. Not a "huge" issue but it is messing around with a few programs. I checked out /etc/udev/rules.d/70-persistent-net.rules and it is as follows

```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x14e4:0x1713 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:38:0d:9f:b9", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4311 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1f:3a:22:b4:e8", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
[B]
# PCI device 0x14e4:0x4311 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1f:3a:22:b4:e8", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
[/B]

```

Now the bolded part is auto added. I have commented it out and it just assigns to eth2 or re adds it. 

Oh yea the stats. ubuntu 8.10

---

### Post by inflamous on 2009-08-20
I have the same problem.  I'm pretty sure its caused by having the wl driver load up before the ssb driver. However you're lucky if your wireless is working, because mine isn't.

---

