---
title: "DWA-542 pci wifi problem: ath9k but no interface"
date: 2009-03-16
forum: Networking &amp; Wireless
---

### Post by tallman7 on 2009-03-16
The first day I installed a PCI wireless card (D-link DWA-542) into my Ubuntu Intrepid 8.10 box, the wifi was auto detected by the 'Network Connections' manager and everything worked fine. However, I have no connection after repeated rebooting. Can anyone tell me what went wrong? I am stumped because it seems ath9k is loading properly, but the wifi network interface is not there. Here are my diagnostics:

# system info 
bash: uname -a
Linux ahti 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux

# lspci shows the card 
bash: lspci | grep "Atheros"
00:09.0 Ethernet controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)  

# after adding ath9k to /etc/modules, it loads on boot
bash: lsmod | grep "ath9k"
ath9k                 296248  0 
mac80211              253440  1 ath9k

# the network interface for the wifi card is 'unclaimed' 
bash: sudo lshw -C network
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32
  *-network:1
       description: Ethernet interface
       product: VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
       vendor: VIA Technologies, Inc.
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: eth0
       version: 11
       serial: 00:50:8d:d1:b5:0f
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-velocity driverversion=1.14 duplex=full latency=32 link=no maxlatency=8 mingnt=3 module=via_velocity multicast=yes port=twisted pair speed=1GB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 32:ba:27:ab:7c:3c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

# Network interfaces
bash: sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:50:8d:d1:b5:0f  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1710 (1.7 KB)
          Interrupt:22 Base address:0xb400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

pan0      Link encap:Ethernet  HWaddr 32:ba:27:ab:7c:3c  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

# no wireless interfaces detected
bash: iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

---

