---
title: "VMWare 1.0.8 &amp; Wireless adapter can't be detected!!"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by tee4cute on 2009-01-12
I'm using Ubuntu 8.10 Intrepid & VMWare Server 1.0.8

After vmware installation, it's only create vmnet0 that's bridged to eth0 (Wired LAN) only and there's no another vmnet that's bridged to my Wireless LAN adapter.

I've tried to config vmware network setting by running script vmware-config.pl. When I'm creating new bridged vmnet on "vmnet2", it shows that in the system has only "ath0 (loop back), pan0 (bluetooth)" adapters can be bridged. 

"So it can't detect my wireless adapter!!!!"

Here is my "lshw" for network :

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5752M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:16:36:f6:1e:71
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5752m-v3.22 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:16:cf:00:35:3a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.5 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 82:1e:55:66:67:f7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

It shows that my wireless adapter is named "wifi0". I tried to force vmware-config to bridge "vmnet2" to "wifi0" but when the vmware starts the system, it shows that the "vmnet2" cannot be initialized and I cannot open the "vmware server console" anymore. It shows that the vmware server is incorrectly installed and I've to remove bridge on "vmnet2" to make "vmware server console" runnable.

Can somebody help me? I'll really appreciate!!! T^T coz now, I can't use WIFI on my vmware T^T

Thanks so much!!

---

