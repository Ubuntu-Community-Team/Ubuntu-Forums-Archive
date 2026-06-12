---
title: "wireless connected - doesn't load in browser"
date: 2011-04-08
forum: Networking &amp; Wireless
---

### Post by annabee on 2011-04-08
This is a new Eee pc 1215T. I'm new to linux - installed ubuntu netbook remix and cannot get my wireless to work. Shows 100%, but will not load anything in any browser. Ethernet is fine. Sorry about not knowing very much... I hope this helps.




anne@Charles:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4313 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 48:5d:60:6d:d1:e8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=172.28.253.7 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:fbefc000-fbefffff
  *-network
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c1
       serial: bc:ae:c5:1b:65:b6
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI duplex=full firmware=N/A ip=137.28.229.200 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:42 memory:fbfc0000-fbffffff ioport:ec00(size=128)




anne@Charles:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:4  Signal level:197  Noise level:167
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0




anne@Charles:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 13d3:5702 IMC Networks 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
anne@Charles:~$

---

