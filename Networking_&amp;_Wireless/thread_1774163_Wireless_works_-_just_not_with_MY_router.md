---
title: "Wireless works - just not with MY router"
date: 2011-06-02
forum: Networking &amp; Wireless
---

### Post by whiffleball on 2011-06-02
I'm using 10.04: wireless networking works brilliantly absolutely anywhere, except with my own router at home. It used to work brilliantly with exactly this router, too ... and all other computers, including Ubuntu boxes, have no problem at all with my home router.

The connection just cuts out all the time - and sporadically is willing to connect for about a minute, out of maybe every hour or so.

This is a weird, pissy little problem. Hope someone is able to help!


|Asus EeePC 1001PXB ~ fully updated Ubuntu 10.04|

lshw -C network gives:
[I]
 *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 74:f0:6d:30:39:a9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.0.65 latency=0 multicast=yes wireless=IEEE 802.11bgn

[/I]

---

