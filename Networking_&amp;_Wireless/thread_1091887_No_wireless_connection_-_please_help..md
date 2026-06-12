---
title: "No wireless connection - please help."
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by mttrnv on 2009-03-09
[B]Got D-link DWA-520 wireless card. Work's fine in Fedora 10, openSUSE 11.1. Fresh install of Ubuntu 8.10 - can't create wireless network.

**mttrnv@mttrnv-linux:~$ sudo lshw -C network**
  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:1f:c6:23:c9:b0
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 duplex=full firmware=N/A latency=0 link=yes module=atl1 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: wifi0
       version: 01
       serial: 00:1e:58:97:37:7e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 02:d2:1e:46:23:ad
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


**After entering command ifconfig appear next info:**

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ppp0      no wireless extensions.

mttrnv@mttrnv-linux:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:1e:58:97:37:7e  
          inet6 addr: fe80::21e:58ff:fe97:377e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1f:c6:23:c9:b0  
          inet6 addr: fec0::8:21f:c6ff:fe23:c9b0/64 Scope:Site
          inet6 addr: 2002:d595:c18:8:21f:c6ff:fe23:c9b0/64 Scope:Global
          inet6 addr: fec0::a:21f:c6ff:fe23:c9b0/64 Scope:Site
          inet6 addr: 2002:d595:1126:a:21f:c6ff:fe23:c9b0/64 Scope:Global
          inet6 addr: 2002:53db:8c64:a:21f:c6ff:fe23:c9b0/64 Scope:Global
          inet6 addr: fe80::21f:c6ff:fe23:c9b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:129353 errors:0 dropped:0 overruns:0 frame:0
          TX packets:886 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:9159256 (9.1 MB)  TX bytes:151968 (151.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14128 (14.1 KB)  TX bytes:14128 (14.1 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:213.149.2.2  P-t-P:83.219.128.0  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:798 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:783447 (783.4 KB)  TX bytes:121710 (121.7 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1E-58-97-37-7E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:2638
          TX packets:589 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:110 (110.0 B)  TX bytes:27719 (27.7 KB)
          Interrupt:18 

**After entering command iwconfig appear next info:**

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ppp0      no wireless extensions.

**Please help fix this problem. Ubuntu -the best, but wireless connection primary option for selecting linux distro for me.Thanx!!!> **

---

