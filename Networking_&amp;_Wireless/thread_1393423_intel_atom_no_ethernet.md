---
title: "intel atom no ethernet"
date: 2010-01-29
forum: Networking &amp; Wireless
---

### Post by BigCdaAnswer3 on 2010-01-29
hey all, i'm not sure if this is the right outlet for my question...
but i'm trying to install karmic on a intel atom (ich7) chipset
but i can't get my ethernet driver (e100) working properly.
it says in dmesg that it's correctly up and given an irq
but that irq is never listed in /proc/interrupts? so dhclient always says "resource temporarily unavailable." i've tried enabling PnP in my bios to no avail...and i haven't found anyone else out there that has a problem with this chipset. does anybody have any suggestions? this almost seems like a bug, but i guess i figured someone else would have probably run into it by now.

---

### Post by chili555 on 2010-01-29
> it says in dmesg that it's correctly upHow about letting us take a look at:```
dmesg | grep e100
dmesg | grep eth
sudo ethtool eth0
```Thanks.

---

### Post by BigCdaAnswer3 on 2010-02-01
I have no way of doing a copy/paste for this machine because this happens during the install process, so here's my best representation of the data:

# dmesg | grep e100
pci 0000:02:08.0: Firmware left e100 interrupts enabled;
e100: 0000:02:02.0 PCI INT A -> GSI 20 (level, low) -> IRQ (screen gets cut off here)
e100: 0000:02:02.0 PME# disabled
e100: eth0: e100_probe: addr 0xfebbff000, irq 20, MAC address ...



The second grep was omitted because it contained the same info as the first...I don't have ethtool because like I said above, this happens during all versions of the 8.10, 9.04, and 9.10 installers (desktop, alternate, netboot, minimal cd image, etc)

based on the command above, you can see that eth0 was given irq 20...however looking at /proc/interrupts, nothing is shown at irq 20. i am completely stumped on this one :(

---

### Post by BigCdaAnswer3 on 2010-02-01
just found the culprit, it was a hardware problem! thanks for the help though.

---

