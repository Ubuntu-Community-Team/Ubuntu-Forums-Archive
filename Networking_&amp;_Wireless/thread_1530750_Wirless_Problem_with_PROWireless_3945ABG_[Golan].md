---
title: "Wirless Problem with PRO/Wireless 3945ABG [Golan]"
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by svprem on 2010-07-14
Hello its been a headache to connect my wireless network for more dhan 2 days..i am searching a solution for this..help me out...

I am using Ubuntu 10.04 my network driver for wireless is as follows...

network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 02
       serial: 00:1f:3c:95:29:e5
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:28 memory:f8000000-f8000fff

i am not able to connect to my personal wifi..

i have tried following steps,

Try 1: Disabled and enabled connection (not working)
Try 2: removed driver and reload it (not working)
Try 3: sudo /etc/init.d/networking restart (not working)
Try 4: Re installed Broadcom packages in Synaptic package manager (no luck even)
Try 5: Re installed network-manager(gnome) (not working too)

my System->Administration->Hardware Drivers show No proprietary drivers are in use on this system..

What should i do further to resolve it...i am out of ideas...Help me..

---

