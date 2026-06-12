---
title: "No Wireless Network Connection"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by rocketbootkid on 2010-01-06
Hi,

I'm new to Ubuntu and have just install Koala on an old PackardBell EasyNote with an Atheros AR5001X onboard PCI Wireless card. From reading all sorts of threads and posts, I think that the hardware is being detected but is not being given an IRQ (if that's correct terminology). See the outputs from various commands below:

dmesg:
[   15.429732] ath_pci 0000:00:06.0: enabling device (0000 -> 0002)
[   15.429745] ath_pci 0000:00:06.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[   15.429794] wifi%d: request_irq failed

lsmod | grep ath:
ath_pci               196788  0 
wlan                  228464  1 ath_pci
ath_hal               362144  1 ath_pci

lspci:
00:06.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

lshw -C network:
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:00:06.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=96 maxlatency=28 mingnt=10
       resources: memory:3c000000-3c00ffff

If anyone can suggest a solution, that would be awesome. I have tried various alterations to menu.lst but to no avail.

Help Ubu-wan, you're my only hope!

---

### Post by rocketbootkid on 2010-01-06
[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)

Suggests, based on "*-network:0 UNCLAIMED", that my driver isn't properly installed, but how do I check?

---

