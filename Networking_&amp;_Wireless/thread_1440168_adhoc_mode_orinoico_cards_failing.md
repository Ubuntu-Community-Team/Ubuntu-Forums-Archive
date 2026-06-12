---
title: "adhoc mode orinoico cards failing"
date: 2010-03-27
forum: Networking &amp; Wireless
---

### Post by ankscorek on 2010-03-27
Hi friends

i have orinocco on two machines...here are the required outputs

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"anks"  Nickname:""
          Mode:Ad-Hoc  Frequency:2.462 GHz  Cell: 02:20:A6:57:58:EA   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/70  Signal level=-48 dBm  Noise level=-93 dBm
          Rx invalid nwid:484  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```



```

ifconfig
ath0      Link encap:Ethernet  HWaddr 00:20:a6:57:58:ea  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::220:a6ff:fe57:58ea/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:23951 (23.9 KB)

eth0      Link encap:Ethernet  HWaddr 00:19:d1:70:be:f2  
          inet addr:10.64.254.107  Bcast:10.64.255.255  Mask:255.255.0.0
          inet6 addr: fe80::219:d1ff:fe70:bef2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16602 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5229 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:5523133 (5.5 MB)  TX bytes:1159788 (1.1 MB)
          Memory:90300000-90320000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12968 (12.9 KB)  TX bytes:12968 (12.9 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-20-A6-57-58-EA-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:78464 errors:0 dropped:0 overruns:0 frame:5398
          TX packets:4027 errors:190 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:15127675 (15.1 MB)  TX bytes:374766 (374.7 KB)
          Interrupt:21 


```



```

dmesg | grep ath0
[   20.716058] ath0: no IPv6 routers present
[ 1377.776008] ath0: no IPv6 routers present
[ 2320.484015] ath0: no IPv6 routers present
[ 2942.392506] ath0: no IPv6 routers present
[ 3267.251523] ath0: unknown SIOCSIWAUTH flag 12
[ 3272.257262] ath0: unknown SIOCSIWAUTH flag 12
[ 3277.263009] ath0: unknown SIOCSIWAUTH flag 12
[ 3282.268780] ath0: unknown SIOCSIWAUTH flag 12
[ 3287.274503] ath0: unknown SIOCSIWAUTH flag 12
[ 3292.278904] ath0: unknown SIOCSIWAUTH flag 12
[ 3297.284645] ath0: unknown SIOCSIWAUTH flag 12
[ 3302.289183] ath0: unknown SIOCSIWAUTH flag 12
[ 3307.292394] ath0: unknown SIOCSIWAUTH flag 12
[ 3312.293150] ath0: unknown SIOCSIWAUTH flag 12
[ 3317.298903] ath0: unknown SIOCSIWAUTH flag 12
[ 3322.302302] ath0: unknown SIOCSIWAUTH flag 12


```


```

lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)
00:03.0 Communication controller: Intel Corporation 82P965/G965 HECI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
02:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b1)
06:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
06:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)


```

PLease Any suggestions to make two orinocco talk to each other in ad-hoc mode

```


lsmod | grep ath
ath_pci               203636  0 
ath_rate_sample        12732  1 
wlan                  226640  4 ath_pci,wlan_scan_sta,ath_rate_sample
ath_hal               303104  3 ath_pci,ath_rate_sample

```
```
 route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
10.64.0.0       0.0.0.0         255.255.0.0     U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         1.1.1.1         0.0.0.0         UG    0      0        0 ath0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 ath0
0.0.0.0         10.64.1.1       0.0.0.0         UG    0      0        0 eth0

```

```
PING 192.168.1.10 (192.168.1.10) 56(84) bytes of data.
From 192.168.1.11 icmp_seq=1 Destination Host Unreachable
From 192.168.1.11 icmp_seq=2 Destination Host Unreachable
From 192.168.1.11 icmp_seq=3 Destination Host Unreachable
From 192.168.1.11 icmp_seq=4 Destination Host Unreachable
From 192.168.1.11 icmp_seq=5 Destination Host Unreachable
From 192.168.1.11 icmp_seq=6 Destination Host Unreachable
From 192.168.1.11 icmp_seq=7 Destination Host Unreachable
From 192.168.1.11 icmp_seq=8 Destination Host Unreachable
From 192.168.1.11 icmp_seq=9 Destination Host Unreachable

```

---

