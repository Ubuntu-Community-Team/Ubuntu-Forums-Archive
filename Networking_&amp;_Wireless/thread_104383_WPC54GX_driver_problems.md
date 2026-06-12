---
title: "WPC54GX driver problems"
date: 2005-12-16
forum: Networking &amp; Wireless
---

### Post by Protoman on 2005-12-16
Alright I have a Linksys WPC54GX Wireless Card w/SRX.  I'm having trouble googlin' up the chipset.  Only things I have found Linux-wise is the WPC54G, and considering the GX has the SRX (Enhanced range + speed) I doubt they are the same.  Was searching other threads and this is what other posters needed to better help the OP's.  Hopefully it is the same here.

lspci -v

0000:05:00.0 Ethernet controller: Unknown device 17cb:0001 (rev 01)
     Subsystem: Linksys: Unknown device 0037
     Flags: medium devsel, IRQ 10
     Memory at 0b080000 (32-bit, non-prefetchable) [disabled] [size=128K]
     Memory at 0b000000 (32-bit, non-prefetchable) [disabled] [size=512k]
     Capabilities: [40] Power Management version 1

And here's what lshw -C network says!

*-network UNCLAIMED
     description: Ethernet controller
     physical id: 0
     bus info: pci@05:00.0
     version: 01
     width: 32 bits
     clock: 33MHz
     capabilites: cap_list
     resources: iomemory:b080000-b09ffff io memory:b000000-b07ffff irq:10

If there is no current support in Ubuntu is their possible going to be future support for it?  Running a 200m+ cable isn't allowed here at my apartment complex (Hell they only let you have one cable outlet....)

---

### Post by Lambert on 2005-12-18
This card is based on the airgo chipset.

It's up to the manufacture of the chipset to release code so someone could write a driver for this. Currently no driver being worked on  for this chipset so even if code is released it will take a while to write a driver and release it. So ubuntu or any other linux distro won't see support for this chipset for a while.

write to linksys and airgo asking them to better support linux.

Matter of fact with the mimo technology, not sure if any linux distro is capable of using a device with mimo technology currenltly.

---

