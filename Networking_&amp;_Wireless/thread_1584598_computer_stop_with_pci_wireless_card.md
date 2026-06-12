---
title: "computer stop with pci wireless card"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by chuchi on 2010-09-29
Hello friends!! I have a SMCWPCI-G2 pci card wireless. And, both in Ubuntu and Windows,at any time, suddenly, the computer stop, blocked completely, and i cannot do nothing. When the card is out, i have no problem. But today, in the Bios, I've found two options about pci: the first one is "PCI Latency Timer" which value is set to "32", and BIOS allows to change this value to 32,64,96,128,160,192,224 and 248. Maybe the "32" value isn't correct, isn't it?? What do you think about? if I change value "32" to other value, Can i solve the problem? I haven't made the change because i am prudent (if I cause an error in the MotherBoard or similar). The second option is "PCI IDE BusMaster" which is set to "Enabled". Many thanks!!

---

### Post by chili555 on 2010-09-29
I have been reading this: [http://www.reric.net/linux/pci_latency.html](http://www.reric.net/linux/pci_latency.html)

It doesn't seem like you can do any damage by changing these values. It will either improve or it will degrade performance. If performance improves, keep adjusting until performance is satisfactory and stop. If performance degrades, back up and stop.

I suggest you try a setting of 64 for PCI Latency Timer and see if performance improves.

I believe that PCI IDE BusMaster set to "Enabled" is correct; I suggest no changes.

---

