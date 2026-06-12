---
title: "Failed detection of Sabrent PCI card in 32/64 bit Lucid?"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by Random Case on 2010-09-04
For a recent PC build, I chose to use the Sabrent PCI-G802 PCI wireless card with a 64-bit installation of Ubuntu Lucid; for installation, the card was inserted into the system before installing Lucid from the mainline 64-bit CD image.

Judging by other posts about this card, the PCI-G802 in this setup does not seem to be detected properly: lspci shows "Network controller: device bfff:3fff" in place of the proper chipset name (i.e., "RaLink RT2561/RT61 802.11g PCI"), while iwconfig and ifconfig show no mention of the device or the wireless connection created under System -> Preferences -> Network Connections (only eth0 and lo loopback, both with "No wireless extensions." to quote iwconfig).  Unsurprisingly, attempts to access the Internet or the router itself via its local IP fail, while the card's activity lights remain dark.  After installing a 32-bit image of Lucid over the prior installation in an attempt to resolve the problem, nothing changes; lspci still reports it as "device bfff:3fff", etc.

If it helps, the motherboard in this build is an Asus M4A77TD.

Output of sudo lshw -C network (skipping the output related to the onboard Ethernet):

```

 *-network UNCLAIMED
   description: Network controller
   physical id: 6
   bus info: pci@0000:03:06.0
   version: 00
   width: 32 bits
   clock: 33MHz
   capabilities: pm bus_master cap_list
   configuration: latency=64
   resources: memory:fbff8000-fbffffff (no IRQ listed there probably explains something)

```

---

