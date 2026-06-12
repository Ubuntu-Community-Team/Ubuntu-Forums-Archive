---
title: "Problems with wireless on Lenovo 3000 G230"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by abcex on 2010-10-26
The problem appeared when I updated to Maverick. It says "wireless is disabled". 

lshw -C network
*-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:16:ea:ae:04:ba
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-22-generic firmware=8.24.2.12 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:44 memory:d4500000-d4501fff

rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Can anyone help? Thanks!

---

