---
title: "Connecting to a WPA network"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by brandon89 on 2008-12-16
Hey guys, I'm having some issues connecting to my roommates wireless network.  From what I can tell its WPA protected and hidden as well (for some reason all the networks are hidden...). So, I've tried connecting to it through the network manager built into ubuntu, but that did not work.  I then switched to WIDC and that still does not find any wireless networks nor will it let me connect to the network if I type it in.  

lshw -C network outputs
> 
 *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1f:e1:a2:c7:b2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg


Some side info, when using windows the network is not hidden.

So any ideas on what I should try?

---

### Post by nixscripter on 2008-12-16
1. Does your friend have MAC address filtering enabled on the network? It might be ignoring your card because it doesn't recognize you.

2. When you connect with network manager, what does the icon do in specific detail?

3. If your computer came with an install CD for the card, you might want to try the windows driver with **ndiswrapper** instead.

---

