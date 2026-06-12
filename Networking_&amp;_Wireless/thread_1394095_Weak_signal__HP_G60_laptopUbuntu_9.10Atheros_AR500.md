---
title: "Weak signal:  HP G60 laptop/Ubuntu 9.10/Atheros AR5001"
date: 2010-01-30
forum: Networking &amp; Wireless
---

### Post by mike2357 on 2010-01-30
Wireless signal strength is quite weak.  When the laptop is a inches from the router it is OK, but moving just a few feet away causes the connection to drop.  Any help would be greatly appreciated.  Specs are as follows:

Machine Brand:  HP G6-458DX laptop

Wireless card info:  Atheros Communications AR5001 Wireless Network Adapter

iwconfig output:
wlan0     IEEE 802.11bg  ESSID:"linksys_XXXXXXX"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:XX:XX:XX:XX:XX   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7  RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=31/70  Signal level=-79 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lshw -C network output:
*-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:XX:XX:XX:XX:XX
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.1.108 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:d2600000-d260ffff

Kernel:  2.6.31-17-generic-pae i686

Thanks much!

---

### Post by mike2357 on 2010-02-20
It turned out to be a hardware problem.  The antenna wires had popped off of the wireless card.  That's why I could connect but only when very close to the router.  Fixing it took a small screw driver and the ten minutes it took to remove the cover, snap the wires back onto the card and replace the cover.  Duh.

---

