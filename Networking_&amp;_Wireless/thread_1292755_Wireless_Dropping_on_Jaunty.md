---
title: "Wireless Dropping on Jaunty"
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by JPKnowMad on 2009-10-16
Alright guys, the forum has been a huge help for me so far so thanks. Here's the problem. I started with Ubuntu 9.04 and I kept dropping my wireless connection about once every ten minutes(it would take a min to reconnect). I figured I would try another OS to see what happened. I went to Fedora 11 and never had the problem. I really love Ubuntu so I decided to come back and try to figure this thing out with the forums help. I am now back on Ubuntu 9.04 and its doing the same thing. I posted what I could below. Thank you in advance for any help and advice. I can't make those smileys go away below, sorry

Acer Aspire 4730Z Laptop

Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

IEEE 802.11bgn  ESSID:"Jim"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:21:29:D5:F9:95   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=68/100  Signal level:-75 dBm  Noise level=-119 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 01
       serial: 00:23:4e:55:78:51
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.1.119 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:d3:24:79
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: be:18:16:8f:d8:55
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

2.6.28-15-generic i686

---

### Post by ericd68 on 2009-10-16
Had a similar issue a while back with my Toshiba Satellite laptop, using the Atheros AR928X. 

Fixed it by installing WICD as the network manager and now it's working pretty much without any dropped connections. Just type in a terminal window

>sudo apt-get install wicd

This will uninstall the default network-manager and install WICD. Configuration is pretty straithforward.

Let me know if this works for you ;-)

---

