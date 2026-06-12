---
title: "Network Unavailable"
date: 2011-03-19
forum: Networking &amp; Wireless
---

### Post by JKyleOKC on 2011-03-19
On the reboot after upgrading my kernel to .30 today, my LAN interface has quit working although the WAN interface is okay (and is how I am posting this). Here are some of the pertinent files:

/etc/network/interfaces:```
auto lo
iface lo inet loopback

iface eth0 inet static
	address 192.168.0.2
	netmask 255.255.255.0
	gateway 192.168.0.2
	post-up iptables-restore < /etc/iptables.up.rules

auto eth0

iface eth1 inet static
#	pre-up /usr/sbin/ethtool -s eth1 autoneg off
	address 66.143.22.33
	netmask 255.255.255.248
	gateway 66.143.22.38

auto eth1


iface eth9 inet static
address 192.168.0.9
netmask 255.255.255.0
gateway 192.168.0.2

auto eth9

```
Output of ifconfig -a:```
eth0      Link encap:Ethernet  HWaddr 00:a0:cc:db:f0:cf  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:ccff:fedb:f0cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:140 errors:1 dropped:0 overruns:0 frame:0
          TX packets:18 errors:6 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000 
          RX bytes:28055 (28.0 KB)  TX bytes:2957 (2.9 KB)
          Interrupt:18 Base address:0xec00 

eth1      Link encap:Ethernet  HWaddr 00:0a:cd:18:bb:7f  
          inet addr:66.143.22.33  Bcast:66.143.22.39  Mask:255.255.255.248
          inet6 addr: fe80::20a:cdff:fe18:bb7f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1138995 (1.1 MB)  TX bytes:173568 (173.5 KB)
          Interrupt:27 

eth9      Link encap:Ethernet  HWaddr 00:26:18:70:fb:c5  
          inet addr:192.168.0.9  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:113 errors:0 dropped:0 overruns:0 frame:0
          TX packets:113 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9647 (9.6 KB)  TX bytes:9647 (9.6 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

ping another box on the LAN:```
jk@mehitabel:~$ ping -c3 192.168.0.5
PING 192.168.0.5 (192.168.0.5) 56(84) bytes of data.
From 192.168.0.9 icmp_seq=1 Destination Host Unreachable
From 192.168.0.9 icmp_seq=2 Destination Host Unreachable
From 192.168.0.9 icmp_seq=3 Destination Host Unreachable

--- 192.168.0.5 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2016ms
, pipe 3
jk@mehitabel:~$ 

```

This box, at 192.168.0.2 on the LAN, serves as my router in addition to being my primary workstation. It has two NICs in addition to the one built into the motherboard. The on-board one is identified as eth9 and is not used at all. The WAN is on eth1 while the LAN is on eth0.

Initially none of the network was responding properly although "ifconfig -a" showed both interfaces as "RUNNING" and indicated small amounts of traffic on each. I've removed NetworkManager completely from the system, and that brought the WAN back to life but has had no effect on the LAN interface, eth0. Nevertheless the ifconfig report above shows a fair amount of traffic over eth0!

Note that my ping report above shows no-response reports from a different IP than I had addressed -- 0.9 rather than 0.5. This is a bit of a puzzle also. And I've tried rolling back to the .29 kernel with absolutely no change of symptoms, which leads me to believe that the failure is associated simply with having rebooted, not with the kernel update itself.

What else can I try, before opening the box and starting to replace NICs?

---

### Post by JKyleOKC on 2011-03-20
Bump, please. It's still a frozen mystery!

---

