---
title: "kubuntu 11.10 eth0 disabled?"
date: 2012-04-12
forum: Networking &amp; Wireless
---

### Post by saturni on 2012-04-12
my ethernet used to work. now it doesn't, probably due to janky updates. i know it's just a matter of editing a file to enable eth0 but i don't which one. plz help!

user1@laptop:~$ sudo lshw -C network
[sudo] password for user1: 
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 90:4c:e5:57:8e:96
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k  driverversion=3.0.0-17-generic firmware=N/A ip=192.168.1.3 latency=0  link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:d3500000-d350ffff
  *-network DISABLED
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=full firmware=N/A latency=0 link=no  multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:d1410000-d1410fff memory:d1400000-d140ffff memory:d1420000-d142ffff
user1@laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000                                                       
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)                                             
          Interrupt:42 Base address:0x2000                                                   

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1696 (1.6 KB)  TX bytes:1696 (1.6 KB)

wlan0     Link encap:Ethernet  HWaddr 90:4c:e5:57:8e:96  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::924c:e5ff:fe57:8e96/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1438083 errors:0 dropped:0 overruns:0 frame:0
          TX packets:780662 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2168808589 (2.1 GB)  TX bytes:70631682 (70.6 MB)

---

### Post by saturni on 2012-04-13
ok, i changed the mac address of eth0 from all zeros to all zeros except the last number i changed to 9. i ran this:
ifconfig eth0 down
ifconfig eth0 hw ether 00:00:00:00:00:09
ifconfig eth0 up
as soon as i hit enter my machine connected through eth0 and is still on line now. what is that about? will i have to do this every time i use eth0? what did that mac address being changed one number have to do with the connection?

---

### Post by dandnsmith on 2012-04-13
Your first posting shows that network as "disabled".
It might have been sufficient to do the eth0 up but!
Check the settings in the network manager or whatever - something must be responsible for that disabled state.

---

