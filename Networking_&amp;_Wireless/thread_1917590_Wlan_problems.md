---
title: "Wlan problems"
date: 2012-01-30
forum: Networking &amp; Wireless
---

### Post by jonttix on 2012-01-30
Hi,

I have HP Elitebook 8440p with Ubuntu 10.04 installed on it. The wireless network is really unstable and right now I can not even see any networks when I scan.

Here are some info:

sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Device or resource busy

pan0      Interface doesn't support scanning.

lshw -C network gives
*-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 06
       serial: 70:5a:b6:ab:7b:e2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=0.12-3 ip=192.168.1.95 latency=0 multicast=yes
       resources: irq:29 memory:d7400000-d741ffff memory:d742a000-d742afff ioport:6020(size=32)
  *-network
       description: Wireless interface
       product: WiFi Link 6000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:44:00.0
       logical name: wlan0
       version: 35
       serial: 00:24:d7:10:bc:70
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:30 memory:d3200000-d3201fff

lspci | grep Network
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
44:00.0 Network controller: Intel Corporation WiFi Link 6000 Series (rev 35)

Please help me!

---

