---
title: "Slow wifi connection in 10.04"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by Mr.Carramba on 2010-08-17
Hi,

After installing 10.04 I get really slower wifi connection, as well as time needed to connect to the base station. I tried with fedora 13 and it worked much more faster.

I have tested changing channels, did the wifi scan to see which channels where occupied as well as looked for activities on them. During the test there where no interference.

It seems that this I am not alone with this problem. 

wlancard
      *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:4000(size=4096) memory:f2500000-f25fffff memory:c0400000-c05fffff(prefetchable)
           *-network DISABLED
                description: Wireless interface
                product: Wireless WiFi Link 5300
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 00
                serial: 00:21:6a:05:f3:2a
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:30 memory:f2500000-f2501fff

---

