---
title: "Wireless firmware missing in Gateway laptop"
date: 2012-09-28
forum: Networking &amp; Wireless
---

### Post by kris kross on 2012-09-28
I recently installed Ubuntu 12.04.1 on my Gateway M350WVN laptop.  I am unable to get a wireless connection, wired is fine.  When I go to system settings and look at the networking section it says 'firmware missing'.   There is nothing listed for 'additional drivers.'  The wireless worked fine before  (my previous OS was windowsxp.)


lspci -nn | grep 'Wireless Brand'  
returns nothing

lspci -nn | grep 'Wireless Brand'
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.


lsmod | grep "wlan_module_name"

returns nothing

sudo lshw -C network
description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:20 memory:e0204000-e0205fff
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 83
       serial: 00:e0:b8:67:9c:ee
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.103 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:e0206000-e0206fff ioport:3000(size=64)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:6b:e4:dc
capabilities: ethernet physical wireless configuration: broadcast=yes driver=b43legacy driverversion=3.2.0-31-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

---

### Post by kris kross on 2012-09-29
Oh yay!  Just figured it out.  I entered the following in the terminal:
sudo apt-get install firmware-b43legacy-installer

Which prompted me to remove some other files and now I have wireless!
We are now safe to walk across the living room without tripping over an ethernet cable. :)

---

