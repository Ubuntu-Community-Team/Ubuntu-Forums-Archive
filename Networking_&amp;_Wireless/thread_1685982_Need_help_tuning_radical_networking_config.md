---
title: "Need help tuning radical networking config"
date: 2011-02-11
forum: Networking &amp; Wireless
---

### Post by Jive Turkey on 2011-02-11
My goal here is to have my headless ubuntu server connect to a wireless AP(router 1) and share that connection to the WAN port of my other router (router 2) which provides internet access to all computers via wired and wireless.  Its currently working well enough for me to post this from a computer with a wired connection to router 2.

I know very little about networking so any help would be greatly appreciated particularly with the static routes on router2.

On my server I have the following:
/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Interface to connect to internet connected wireless AP
auto wlan0
iface wlan0 inet dhcp
        wireless-essid dd-wrt
        wireless-mode managed
 pre-up /home/jiveturkey/iptablesICS.sh


# Internal network interface for private subnet(10.0.0.0/24)
# 1000/100 speed interface for miscellaneous LAN services
auto eth0
iface eth0 inet dhcp

# Interface to be connected to WAN port (having 10.10.0.2) of the internal router/wireless AP
# Its a 100/10 speed PCI card I salvaged from a PC I found in the garbage.
auto eth1
iface eth1 inet static
        address 10.10.0.1
        netmask 255.255.255.0
        network 10.10.0.0

```
The script iptablesICS.sh called by "pre-up /..." contains:```

#!/bin/sh
## wlan0 has the IP 192.168.1.102 statically assigned by router1
## eth0 has the IP 10.0.0.100 statically assigned by router2
## eth1 has the IP 10.10.0.1 and the WAN port of the second router has 10.10.0.2 (static addresses)
iptables -A FORWARD -o wlan0 -i eth1 -s 10.10.0.0/24 -m conntrack --ctstate NEW -j ACCEPT
iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A POSTROUTING -t nat -j MASQUERADE

```
Also, I added the following lines to /etc/sysctl.conf:
```

net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1
net.ipv4.ip_forward=1

```
On router2 I created the following static routes:
```

  	# 	Active 	Name 	Destination 	Gateway
 	1	Yes	ICS-route2 	192.168.1.1	10.0.0.1
 	2	Yes	ICS-route 	192.168.1.0	10.10.0.1

```
For testing purposes I created "testingICS.sh":
```

#!/bin/sh
echo "** ifconfig"
ifconfig wlan0
ifconfig eth1
ifconfig eth0
echo '\n'
echo "** route"
route
echo '\n'
echo "** iptables -L"
iptables -L
echo '\n'
echo "** ping first router from wlan0"
ping -c3 -I wlan0 192.168.1.1
echo '\n'
echo "** ping google from wlan0"
ping -c3 -I wlan0 www.google.com
echo '\n'
echo "** ping 2nd router from eth1"
ping -c3 -I eth1 10.10.0.2
echo '\n'
echo "** ping router1, router2, & google from eth0"
ping -c3 -I eth0 192.168.1.1
ping -c3 -I eth0 10.0.0.1
ping -c3 -I eth0 www.google.com

```
I get the results:
```

** ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:0e:3b:0a:58:5d  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:3bff:fe0a:585d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28956 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47810 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6771063 (6.7 MB)  TX bytes:6654160 (6.6 MB)

eth1      Link encap:Ethernet  HWaddr 00:60:67:73:b6:c5  
          inet addr:10.10.0.1  Bcast:10.10.0.255  Mask:255.255.255.0
          inet6 addr: fe80::260:67ff:fe73:b6c5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1524 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1800 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:153729 (153.7 KB)  TX bytes:1547446 (1.5 MB)
          Interrupt:17 Base address:0xd000 

eth0      Link encap:Ethernet  HWaddr 00:27:0e:0b:57:bb  
          inet addr:10.0.0.100  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::227:eff:fe0b:57bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:289307 errors:0 dropped:0 overruns:0 frame:0
          TX packets:420555 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31960001 (31.9 MB)  TX bytes:469510857 (469.5 MB)
          Interrupt:43 



** route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
10.10.0.0       *               255.255.255.0   U     0      0        0 eth1
default         DD-WRT          0.0.0.0         UG    100    0        0 wlan0
default         10.0.0.1        0.0.0.0         UG    100    0        0 eth0


** iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  10.10.0.0/24         anywhere            ctstate NEW 
ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


** ping first router from wlan0
PING 192.168.1.1 (192.168.1.1) from 192.168.1.102 wlan0: 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=5.23 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=3.40 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=1.16 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 1.161/3.267/5.234/1.665 ms


** ping google from wlan0
PING www.l.google.com (74.125.65.105) from 192.168.1.102 wlan0: 56(84) bytes of data.
64 bytes from gx-in-f105.1e100.net (74.125.65.105): icmp_req=1 ttl=53 time=29.6 ms
64 bytes from gx-in-f105.1e100.net (74.125.65.105): icmp_req=2 ttl=53 time=43.0 ms
64 bytes from gx-in-f105.1e100.net (74.125.65.105): icmp_req=3 ttl=53 time=26.9 ms

--- www.l.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 26.941/33.221/43.074/7.054 ms


** ping 2nd router from eth1
PING 10.10.0.2 (10.10.0.2) from 10.10.0.1 eth1: 56(84) bytes of data.
64 bytes from 10.10.0.2: icmp_req=1 ttl=64 time=0.238 ms
64 bytes from 10.10.0.2: icmp_req=2 ttl=64 time=0.222 ms
64 bytes from 10.10.0.2: icmp_req=3 ttl=64 time=0.224 ms

--- 10.10.0.2 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.222/0.228/0.238/0.007 ms


** ping router1, router2, & google from eth0
PING 192.168.1.1 (192.168.1.1) from 10.0.0.100 eth0: 56(84) bytes of data.
From 10.0.0.1: icmp_seq=1 Redirect Host(New nexthop: 192.168.1.1)
From 10.0.0.1: icmp_seq=2 Redirect Host(New nexthop: 192.168.1.1)
From 10.0.0.1: icmp_seq=3 Redirect Host(New nexthop: 192.168.1.1)
[COLOR="red"]From 10.0.0.1 icmp_seq=1 Destination Host Unreachable
From 10.0.0.1 icmp_seq=2 Destination Host Unreachable
From 10.0.0.1 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2006ms[/COLOR]
pipe 3
PING 10.0.0.1 (10.0.0.1) from 10.0.0.100 eth0: 56(84) bytes of data.
64 bytes from 10.0.0.1: icmp_req=1 ttl=64 time=0.171 ms
64 bytes from 10.0.0.1: icmp_req=2 ttl=64 time=0.208 ms
64 bytes from 10.0.0.1: icmp_req=3 ttl=64 time=0.195 ms

--- 10.0.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.171/0.191/0.208/0.019 ms
PING www.l.google.com (74.125.65.104) from 10.0.0.100 eth0: 56(84) bytes of data.

[COLOR="Red"]--- www.l.google.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2001ms[/COLOR]

```

Any all feedback to help me set this up correctly would be greatly appreciated.  I'm currently posting this from a Windows7 PC connected to the second router so I know this is partly right.

---

