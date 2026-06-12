---
title: "wlan0 appears but cant get Ip, Netgear:WG311.v3"
date: 2012-12-26
forum: Networking &amp; Wireless
---

### Post by christiansenk on 2012-12-26
Hi All,
Have followed various setups for the above pci card and installed the win 2000 drivers as suggested.
Currently I:
can "see neighbour's AP" in wireless networking. but not my own SSID
I have a cable / DSL connection which works to my router (192.168.2.1)
I have the following outputs:

lspci output:
 02:05.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

kim@linux:~$ iwconfig
lo        no wireless extensions.

ham0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

kim@linux:~$ sudo iwlist wlan0 scan
wlan0     No scan results

kim@linux:~$ sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: wlan0
       version: 03
       serial: 00:1e:2a:b5:25:12
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wg311v3 driverversion=1.57+NETGEAR,02/22/2005,3.1.1.7 latency=64k=no multicast=yes wireless=IEEE 802.11g
       resources: irq:20 memory:fddd0000-fdddffff memory:fdde0000-fddeffff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 10
       serial: 00:15:58:46:19:98
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.10 ncy=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:22 ioport:de00(size=256) memory:fddff000-fddff0ff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: ham0
       serial: 7a:79:19:69:b4:65
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full firmware=N/A ip=25.105.101 link=yes multicast=yes port=twisted pair speed=10Mbit/s
=====================================
Any help is greatly appreciated.

---

