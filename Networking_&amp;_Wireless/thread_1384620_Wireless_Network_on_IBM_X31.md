---
title: "Wireless Network on IBM X31??"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by Peden on 2010-01-18
Hi everybody.. 

I have a problem, i cant get my wifi card on my X31 to work?? I have used approx a day to read on the internet to find a solution?

I have tried to add this to the blacklist file:
"# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes"

it didn't work... I have tried to download many different files/packages/program that people had recommended.. But i dont know have it works?? 



 sudo lshw -C network 
  *-network:0 UNCLAIMED   
       description: Network controller
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd cap_list
       configuration: latency=64 maxlatency=4 mingnt=4
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:09:6b:fa:fe:82
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.101.127 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s


Hope somebody can help me??

---

### Post by chili555 on 2010-01-18
First, Network Manager is designed to *not* allow a wireless connection if you have a wired connection, which you do. When we get a proper driver loaded and your Aironet is no longer UNCLAIMED (unclaimed by an appropriate driver), you will need to disconnect the ethernet cable in order to get the wireless to connect. 

Let's see what the kernel says is going on. Please open a terminal and do:```
sudo modprobe airo
dmesg | grep -i airo
dmesg | grep host
```Post the result and we'll see if we can fix it!

---

