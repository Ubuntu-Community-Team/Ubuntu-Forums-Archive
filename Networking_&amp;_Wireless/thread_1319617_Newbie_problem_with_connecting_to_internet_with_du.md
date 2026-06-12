---
title: "Newbie problem with connecting to internet with dual boot netbook remix 9.04"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by cmrusink on 2009-11-08
I recently bought an Acer Aspire One D250-1151 and created a dual boot with Netbook Remix 9.04 and cannot connect to the internet.  My kernel version is "2.6.28-11-generic".
I tried following directions using ndiswrapper-1.55 to load a new driver, but could not find a driver for a AR9285 adapter on the ndiswrapper site.

lspci -v shows:
01:00.0  Network controller: Atheros Communications Inc.  AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
             Subsystem: Foxconn International, Inc. Device e016
             Flags: bus master, fast devsel, latency 0, IRQ 11
             Memory at 57100000 (64-bit, non-prefetchable) [size=64K]
             Capabilities: <access denied>

ifconfig only shows the loopback

iwconfig shows:
lo          no wireless extensions.

pan0     no wireless extensions.

sudo lshw -C network shows:
*-network UNCLAIMED
         description: Network controller
         product: AR9285 Wireless Network Adapter (PCI-Express)
         vendor: Atheros Communications Inc.
         physical id: 0
         bus info: pci@0000:01:00.0
         version: 01
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress bus_master cap_list
         configuration: latency=0

Also, the Ethernet controller comes up:
*-network UNCLAIMED


Any help or direction would be great!

---

