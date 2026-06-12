---
title: "Limited Wi-Fi Connectivity under Linux"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by chessnerd on 2009-11-24
My laptop has been having issues with networking under Ubuntu. The biggest problem I have is with the Wi-Fi card - it works only half a well as it does under Windows.

In my room at home the wireless router is all the way across the house so under Windows the wireless works at about 50%, the connection rarely needs to be restarted (maybe once every hour on a bad day) and I find any difficulties to be very tolerable.

On the Linux partition, the connection monitor usually runs between 22% and 28% in my room and the connection is hit and miss most of the time. Last night, it took over an hour to download 51 MB of updates. That, in my opinion, is intolerable.

I'm in my kitchen at the moment, about 5 feet from the router, and it is still only at 81%. It should easily be at 100% when I'm this close.

I'm using an Atheros AR928X card. 

lspci for the card:
```
04:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```

and lshw -c Network returns this:
```
*-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 01
       serial: 00:23:4d:13:eb:8d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f1000000-f100ffff
```

So, is there anything I could do to improve my wireless connection under Ubuntu?

---

### Post by chessnerd on 2009-11-29
Still having this issue if anyone would like to take a stab at it.

---

