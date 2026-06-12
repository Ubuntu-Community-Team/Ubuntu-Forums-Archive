---
title: "WiFi on Dell E6400"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by giesen2 on 2009-11-03
With Ubuntu 9.04 on my Dell E6400, WiFi worked automatically without any manual configuration steps...

I did a clean reinstall of 9.10 and WiFi isn't working.

I see the following from lshw... Not sure what's wrong or where to go from here... Thanks!

          *-network
                description: Network controller
                product: BCM4322 802.11a/b/g/n Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0
                resources: irq:17 memory:f69fc000-f69fffff

---

