---
title: "Wired network eth0 disappeared"
date: 2012-07-02
forum: Networking &amp; Wireless
---

### Post by theunsheydenrych on 2012-07-02
HI
After a 12.04 update last week that included a kernel update, my wireless stop to work i connected with a wire to the internet and followed the steps here [http://askubuntu.com/questions/135174/ubuntu-12-04-broadcom-wireless-not-working-after-b43](http://askubuntu.com/questions/135174/ubuntu-12-04-broadcom-wireless-not-working-after-b43) to rectify the problem.

Now my wired network is not working?

sudo lshw -C network shows this.
*-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f4000000-f4003fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:f4108000-f4109fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:14:e1:55
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-26-generic-pae firmware=508.1084 ip=192.168.0.5 link=yes multicast=yes wireless=IEEE 802.11bg

Please help? 
How can i fix this?

Regards

---

### Post by theunsheydenrych on 2012-07-03
I searched in the /etc/modprobe.d/ directory for b44 with the following command
grep b44 * 
and found the b44 was blacklisted in the  broadcom-sta-common.conf file.
I commented the line out and reboot, now the eth0 is back.

---

