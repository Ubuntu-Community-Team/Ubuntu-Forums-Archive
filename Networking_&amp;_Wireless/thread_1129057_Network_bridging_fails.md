---
title: "Network bridging fails"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by Jochus on 2009-04-18
Hi,

First of all, let me tell you that I really search a lot on the internet, and I got a lot information on these 2 pages:

[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

So, I have a wireless controller (WMP95G - Linksys) which is connected to my router. It totally works fine!
Then I have a RTL-8139 (RealTek) ethernet controller which is connected to a hub. I want the RTL ethernet bridged with the wireless controller, so people on the hub will be able to access the router

So, this is my /etc/network/interfaces file

```

auto lo
iface lo inet loopback
 
auto eth0
auto wlan0
auto br0
 
iface eth0 inet manual
 
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid ##HIDDEN##
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk ##HIDDEN##
 
iface br0 inet static
bridge-ports wlan0 eth0
address 192.168.1.100
netmask 255.255.255.0

```

I'm not able to connect on the PC with my router after executing an /etc/init.d/networking restart

```

jochus@passoa /etc/network $ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
 
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:23:69:01:b8:8b
Sending on   LPF/wlan0/00:23:69:01:b8:8b
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
 * if-up.d/mountnfs[eth0]: waiting for interface wlan0 before doing NFS mounts
 * if-up.d/mountnfs[eth0]: waiting for interface br0 before doing NFS mounts
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
 
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:23:69:01:b8:8b
Sending on   LPF/wlan0/00:23:69:01:b8:8b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.1.109 from 192.168.1.1
DHCPREQUEST of 192.168.1.109 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.109 from 192.168.1.1
bound to 192.168.1.109 -- renewal in 41271 seconds.
 * if-up.d/mountnfs[wlan0]: waiting for interface br0 before doing NFS mounts
 
Waiting for br0 to get ready (MAXWAIT is 32 seconds).
                                                                         [ OK ]

```

dmesg info

```

jochus@passoa /etc/network $ dmesg
[   24.609644] lo: Disabled Privacy Extensions
[   24.611629] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.843387] wlan0: authenticate with AP 00:16:b6:3b:1e:3c
[   24.847384] wlan0: authenticated
[   24.847395] wlan0: associate with AP 00:16:b6:3b:1e:3c
[   24.849622] wlan0: RX AssocResp from 00:16:b6:3b:1e:3c (capab=0x411 status=0 
aid=1)
[   24.849630] wlan0: associated
[   24.852478] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   25.644419] ACPI: WMI: Mapper loaded
[   25.954701] padlock: VIA PadLock not detected.
[   27.265279] warning: `avahi-daemon' uses 32-bit capabilities (legacy support 
in use)
[   29.778041] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   29.778055] apm: overridden by ACPI.
[   30.049646] ppdev: user-space parallel port driver
[   35.568042] wlan0: no IPv6 routers present
[   41.260774] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[   52.208018] eth0: no IPv6 routers present
[ 1015.057028] wlan0: deauthenticating by local choice (reason=3)
[ 1015.261566] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1016.010932] wlan0: authenticate with AP 00:16:b6:3b:1e:3c
[ 1016.015509] wlan0: authenticated
[ 1016.015522] wlan0: associate with AP 00:16:b6:3b:1e:3c
[ 1016.018417] wlan0: RX AssocResp from 00:16:b6:3b:1e:3c (capab=0x411 status=0 
aid=1)
[ 1016.018428] wlan0: associated
[ 1016.018825] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1017.713256] Bridge firewalling registered
[ 1017.713921] br0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[ 1017.721786] device wlan0 entered promiscuous mode
[ 1017.732289] device eth0 entered promiscuous mode
[ 1017.738150] br0: port 2(eth0) entering learning state
[ 1017.738180] br0: port 1(wlan0) entering learning state
[ 1026.904030] wlan0: no IPv6 routers present
[ 1028.056030] br0: no IPv6 routers present
[ 1032.736029] br0: topology change detected, propagating
[ 1032.736042] br0: port 2(eth0) entering forwarding state
[ 1032.736046] br0: topology change detected, propagating
[ 1032.736050] br0: port 1(wlan0) entering forwarding state

```

/var/log/messages

```

Apr 18 10:44:04 passoa kernel: [ 1129.429601] br0: port 1(wlan0) entering disabl
ed state
Apr 18 10:44:04 passoa kernel: [ 1129.500881] br0: port 2(eth0) entering disable
d state
Apr 18 10:44:04 passoa kernel: [ 1129.532812] device wlan0 left promiscuous mode
Apr 18 10:44:04 passoa kernel: [ 1129.532839] br0: port 1(wlan0) entering disabl
ed state
Apr 18 10:44:05 passoa kernel: [ 1129.547640] device eth0 left promiscuous mode
Apr 18 10:44:05 passoa kernel: [ 1129.547667] br0: port 2(eth0) entering disable
d state
Apr 18 10:44:05 passoa kernel: [ 1129.575633] eth0: link up, 10Mbps, half-duplex
, lpa 0x0000
Apr 18 10:44:05 passoa kernel: [ 1129.785529] ADDRCONF(NETDEV_UP): wlan0: link i
s not ready
Apr 18 10:44:06 passoa kernel: [ 1130.543837] ADDRCONF(NETDEV_CHANGE): wlan0: li
nk becomes ready
Apr 18 10:44:10 passoa kernel: [ 1134.797933] device wlan0 entered promiscuous mode
Apr 18 10:44:10 passoa kernel: [ 1134.807177] device eth0 entered promiscuous mode
Apr 18 10:44:10 passoa kernel: [ 1134.814243] br0: port 2(eth0) entering learning state
Apr 18 10:44:10 passoa kernel: [ 1134.814270] br0: port 1(wlan0) entering learning state
Apr 18 10:44:25 passoa kernel: [ 1149.812034] br0: topology change detected, propagating
Apr 18 10:44:25 passoa kernel: [ 1149.812047] br0: port 2(eth0) entering forwarding state
Apr 18 10:44:25 passoa kernel: [ 1149.812051] br0: topology change detected, propagating
Apr 18 10:44:25 passoa kernel: [ 1149.812055] br0: port 1(wlan0) entering forwarding state

```

ifconfig -a

```

jochus@passoa /etc/network $ ifconfig -a
br0       Link encap:Ethernet  HWaddr 00:10:dc:2d:bc:5d  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:dcff:fe2d:bc5d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1192 (1.1 KB)  TX bytes:3636 (3.6 KB)
 
eth0      Link encap:Ethernet  HWaddr 00:10:dc:2d:bc:5d  
          inet6 addr: fe80::210:dcff:fe2d:bc5d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:316 errors:0 dropped:0 overruns:0 frame:0
          TX packets:719 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33055 (33.0 KB)  TX bytes:86295 (86.2 KB)
          Interrupt:21 Base address:0xc000 
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3209 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3209 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:652008 (652.0 KB)  TX bytes:652008 (652.0 KB)
 
wlan0     Link encap:Ethernet  HWaddr 00:23:69:01:b8:8b  
          inet6 addr: fe80::223:69ff:fe01:b88b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1785 errors:0 dropped:0 overruns:0 frame:0
          TX packets:513 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:241928 (241.9 KB)  TX bytes:73363 (73.3 KB)
 
wmaster0  Link encap:UNSPEC  HWaddr 00-23-69-01-B8-8B-38-38-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Any idea's what I'm doing wrong? I'm really stuck on this problem ...

---

### Post by Jochus on 2009-04-26
Ok, I tried the exact same configuration on my portable and it also didn't work on Ubuntu. When I rebooted to Windows, I could create a network bridge in exactly 60 seconds. Just select your wired and wireless connection. Right click on it and choose "create networkbridge"

So the hardware is capable for briding, why isn't my Ubuntu setting capable?

---

### Post by Jochus on 2009-04-28
Ok, I made it myself a little easier by temporarly switching from WPA2 to unsecure wireless networking.

I'm having the following configuration:

```

to lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto eth1
iface eth1 inet manual
wireless-essid ##MY-ESSID##
wireless-mode managed

auto br0
iface br0 inet dhcp
bridge_ports eth0, eth1
```

When I reboot, my interfaces are getting the following config:

```

br0       Link encap:Ethernet  HWaddr 00:0a:e4:ae:7e:4c  
          inet6 addr: fe80::20a:e4ff:feae:7e4c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:87 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17544 (17.1 KB)  TX bytes:3744 (3.6 KB)

br0:avahi Link encap:Ethernet  HWaddr 00:0a:e4:ae:7e:4c  
          inet addr:169.254.7.81  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:0a:e4:ae:7e:4c  
          inet6 addr: fe80::20a:e4ff:feae:7e4c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1770 (1.7 KB)  TX bytes:23069 (22.5 KB)
          Interrupt:20 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:15:00:1f:20:a6  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:ff:fe1f:20a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:223 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18762 (18.3 KB)  TX bytes:8392 (8.1 KB)
          Interrupt:21 Base address:0xa000 Memory:c8006000-c8006fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1879 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1879 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:94956 (92.7 KB)  TX bytes:94956 (92.7 KB

```

The bridge looks ok:

```

jochus@Bacardi ~ $ sudo brctl show br0
[sudo] password for jochus: 
bridge name     bridge id               STP enabled     interfaces
br0             8000.000ae4ae7e4c       no              eth0
                                                        eth1

```

My routing table looks like this:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 br0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 br0
```

But I'm not able to ping my router :-( ...

```

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.111 icmp_seq=1 Destination Host Unreachable
From 192.168.1.111 icmp_seq=2 Destination Host Unreachable
From 192.168.1.111 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4018ms

```

Anybody some idea's?

---

### Post by Jochus on 2009-04-28
I tried sniffing the interfaces br0, eth0 and eth1 with Wireshark. This is the result after restarting the networking daemon

br0

```

1	0.000000000	fe80::20a:e4ff:feae:7e4c	ff02::2	ICMPv6	Router solicitation
2	24.824098000	0.0.0.0	255.255.255.255	DHCP	DHCP Discover - Transaction ID 0xa117a72
3	28.824043000	0.0.0.0	255.255.255.255	DHCP	DHCP Discover - Transaction ID 0xa117a72
4	33.685106000	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
5	33.688946000	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
6	33.692700000	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
7	33.698081000	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
8	33.701656000	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
9	33.705492000	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
10	33.708885000	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
11	33.712502000	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
12	33.716242000	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
13	33.719929000	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
14	38.824050000	0.0.0.0	255.255.255.255	DHCP	DHCP Discover - Transaction ID 0xa117a72
15	48.824039000	0.0.0.0	255.255.255.255	DHCP	DHCP Discover - Transaction ID 0xa117a72
16	56.768033000	Wistron_ae:7e:4c	Broadcast	ARP	Who has 169.254.7.81?  Tell 0.0.0.0
17	57.992048000	Wistron_ae:7e:4c	Broadcast	ARP	Who has 169.254.7.81?  Tell 0.0.0.0
18	59.019954000	Wistron_ae:7e:4c	Broadcast	ARP	Who has 169.254.7.81?  Tell 0.0.0.0
19	61.020124000	Wistron_ae:7e:4c	Broadcast	ARP	Gratuitous ARP for 169.254.7.81 (Request)
20	62.004532000	169.254.7.81	169.254.255.255	NBNS	Registration NB BACARDI<20>
21	62.004582000	169.254.7.81	169.254.255.255	NBNS	Registration NB BACARDI<03>
22	62.004615000	169.254.7.81	169.254.255.255	NBNS	Registration NB BACARDI<00>
23	62.004647000	169.254.7.81	169.254.255.255	NBNS	Registration NB MSHOME<00>
24	62.004679000	169.254.7.81	169.254.255.255	NBNS	Registration NB MSHOME<1e>
25	62.004775000	169.254.7.81	169.254.255.255	BROWSER	Host Announcement BACARDI, Workstation, Server, Print Queue Server, Xenix Server, NT Workstation, NT Server, Potential Browser, Unknown server type:23
26	63.023921000	Wistron_ae:7e:4c	Broadcast	ARP	Gratuitous ARP for 169.254.7.81 (Request)
27	64.003996000	169.254.7.81	169.254.255.255	NBNS	Registration NB BACARDI<20>
28	64.004033000	169.254.7.81	169.254.255.255	NBNS	Registration NB BACARDI<03>
29	64.004054000	169.254.7.81	169.254.255.255	NBNS	Registration NB BACARDI<00>
30	64.004075000	169.254.7.81	169.254.255.255	NBNS	Registration NB MSHOME<00>
31	64.004097000	169.254.7.81	169.254.255.255	NBNS	Registration NB MSHOME<1e>
32	64.004156000	169.254.7.81	169.254.255.255	NBNS	Registration NB BACARDI<20>
33	64.004179000	169.254.7.81	169.254.255.255	NBNS	Registration NB BACARDI<03>
34	64.004200000	169.254.7.81	169.254.255.255	NBNS	Registration NB BACARDI<00>
35	64.004220000	169.254.7.81	169.254.255.255	NBNS	Registration NB MSHOME<00>
36	64.004240000	169.254.7.81	169.254.255.255	NBNS	Registration NB MSHOME<1e>
37	65.127895000	Wistron_ae:7e:4c	Broadcast	ARP	Who has 195.130.129.165?  Tell 169.254.7.81
38	66.004121000	169.254.7.81	169.254.255.255	NBNS	Registration NB BACARDI<20>
39	66.004177000	169.254.7.81	169.254.255.255	NBNS	Registration NB BACARDI<03>
40	66.004197000	169.254.7.81	169.254.255.255	NBNS	Registration NB BACARDI<00>
41	66.004219000	169.254.7.81	169.254.255.255	NBNS	Registration NB MSHOME<00>
42	66.004239000	169.254.7.81	169.254.255.255	NBNS	Registration NB MSHOME<1e>
43	66.127931000	Wistron_ae:7e:4c	Broadcast	ARP	Who has 195.130.129.165?  Tell 169.254.7.81
44	67.127989000	Wistron_ae:7e:4c	Broadcast	ARP	Who has 195.130.129.165?  Tell 169.254.7.81
45	70.127967000	Wistron_ae:7e:4c	Broadcast	ARP	Who has 195.130.130.165?  Tell 169.254.7.81
46	71.128025000	Wistron_ae:7e:4c	Broadcast	ARP	Who has 195.130.130.165?  Tell 169.254.7.81


```

eth0

```

1	0.000000	Wistron_ae:7e:4c	Broadcast	ARP	Who has 192.168.1.1?  Tell 192.168.1.112
2	19.840146	0.0.0.0	255.255.255.255	DHCP	DHCP Discover - Transaction ID 0x8537ad48
3	24.840168	0.0.0.0	255.255.255.255	DHCP	DHCP Discover - Transaction ID 0x8537ad48
4	38.840099	0.0.0.0	255.255.255.255	DHCP	DHCP Discover - Transaction ID 0x8537ad48
5	45.513321	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
6	45.516537	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
7	45.520384	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
8	45.524058	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
9	45.527325	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
10	45.530872	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
11	45.534676	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
12	45.538019	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
13	45.541774	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
14	45.545417	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
15	45.549231	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
16	51.412036	Wistron_ae:7e:4c	Broadcast	ARP	Who has 169.254.7.81?  Tell 0.0.0.0
17	53.360036	Wistron_ae:7e:4c	Broadcast	ARP	Who has 169.254.7.81?  Tell 0.0.0.0
18	54.716034	Wistron_ae:7e:4c	Broadcast	ARP	Who has 169.254.7.81?  Tell 0.0.0.0
19	56.716135	Wistron_ae:7e:4c	Broadcast	ARP	Gratuitous ARP for 169.254.7.81 (Request)
20	58.716070	Wistron_ae:7e:4c	Broadcast	ARP	Gratuitous ARP for 169.254.7.81 (Request)
21	60.775980	Wistron_ae:7e:4c	Broadcast	ARP	Who has 195.130.129.165?  Tell 169.254.7.81

```

eth1

```

1	0.000000	fe80::215:ff:fe1f:20a6	ff02::2	ICMPv6	Router solicitation
2	25.983879	0.0.0.0	255.255.255.255	DHCP	DHCP Discover - Transaction ID 0xe2640e1c
3	30.983864	0.0.0.0	255.255.255.255	DHCP	DHCP Discover - Transaction ID 0xe2640e1c
4	32.949057	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
5	32.952404	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
6	32.957215	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
7	32.960893	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
8	32.964222	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
9	32.970023	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
10	32.973868	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
11	32.977056	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
12	32.981455	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
13	32.985056	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
14	32.988717	192.168.1.1	239.255.255.250	SSDP	NOTIFY * HTTP/1.1  
15	44.983895	0.0.0.0	255.255.255.255	DHCP	DHCP Discover - Transaction ID 0xe2640e1c
16	54.983846	0.0.0.0	255.255.255.255	DHCP	DHCP Discover - Transaction ID 0xe2640e1c
17	57.199856	Wistron_ae:7e:4c	Broadcast	ARP	Who has 169.254.7.81?  Tell 0.0.0.0
18	58.967801	Wistron_ae:7e:4c	Broadcast	ARP	Who has 169.254.7.81?  Tell 0.0.0.0
19	60.039785	Wistron_ae:7e:4c	Broadcast	ARP	Who has 169.254.7.81?  Tell 0.0.0.0
20	62.039897	Wistron_ae:7e:4c	Broadcast	ARP	Gratuitous ARP for 169.254.7.81 (Request)
21	64.039860	Wistron_ae:7e:4c	Broadcast	ARP	Gratuitous ARP for 169.254.7.81 (Request)
22	66.107737	Wistron_ae:7e:4c	Broadcast	ARP	Who has 195.130.129.165?  Tell 169.254.7.81
23	66.164183	169.254.7.81	169.254.255.255	NBNS	Registration NB BACARDI<20>
24	66.164203	169.254.7.81	169.254.255.255	NBNS	Registration NB BACARDI<03>
25	66.164222	169.254.7.81	169.254.255.255	NBNS	Registration NB BACARDI<00>
26	66.164241	169.254.7.81	169.254.255.255	NBNS	Registration NB MSHOME<00>
27	66.164258	169.254.7.81	169.254.255.255	NBNS	Registration NB MSHOME<1e>
28	66.164314	169.254.7.81	169.254.255.255	BROWSER	Host Announcement BACARDI, Workstation, Server, Print Queue Server, Xenix Server, NT Workstation, NT Server, Potential Browser, Unknown server type:23


```

---

