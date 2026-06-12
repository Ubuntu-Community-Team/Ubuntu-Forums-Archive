---
title: "AR5008EG Not Working"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by arleslie on 2009-04-27
I have an Acer Aspire One with wireless adapter Atheros AR5008EG. Ubuntu verison: 9.01 [Upgraded from Ubuntu 8.10 WUBI], Ubuntu 8.10 installed the driver for AR5007EG but it still wouldn't work so I upgraded to Ubuntu 9.01 and saw I can add the Windows Drivers for it so I downloaded the windows drivers and it says that the Hardware is present but on the start it says "Unable to see if hardware is present" I have installed the correct drivers but ifconfig doesn't show the card at all, when I click on the networking icon it only shows Wired Network.

I went to Hardware Drivers and saw that I could use ath5k driver from MadWifi but it still didn't work.

Heres a lshw report 
>        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet controller
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list
                configuration: driver=ndiswrapper latency=0 module=ndiswrapper


---

