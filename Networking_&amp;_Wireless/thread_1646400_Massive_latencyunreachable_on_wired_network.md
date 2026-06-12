---
title: "Massive latency/unreachable on wired network"
date: 2010-12-15
forum: Networking &amp; Wireless
---

### Post by Kjella on 2010-12-15
I'm experiencing massive latency/unreachable problems on my Linux machine. It's true for all network connections, here's an example of me trying to ping my router:

PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=15115 ms
64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=14107 ms
64 bytes from 192.168.0.1: icmp_req=3 ttl=64 time=13107 ms
64 bytes from 192.168.0.1: icmp_req=4 ttl=64 time=12107 ms
64 bytes from 192.168.0.1: icmp_req=5 ttl=64 time=11108 ms
64 bytes from 192.168.0.1: icmp_req=6 ttl=64 time=10108 ms
64 bytes from 192.168.0.1: icmp_req=7 ttl=64 time=9108 ms
64 bytes from 192.168.0.1: icmp_req=8 ttl=64 time=8108 ms
64 bytes from 192.168.0.1: icmp_req=9 ttl=64 time=7108 ms
64 bytes from 192.168.0.1: icmp_req=10 ttl=64 time=6108 ms
64 bytes from 192.168.0.1: icmp_req=11 ttl=64 time=5108 ms
64 bytes from 192.168.0.1: icmp_req=12 ttl=64 time=4109 ms
64 bytes from 192.168.0.1: icmp_req=13 ttl=64 time=3109 ms
64 bytes from 192.168.0.1: icmp_req=14 ttl=64 time=2109 ms
64 bytes from 192.168.0.1: icmp_req=15 ttl=64 time=1109 ms
64 bytes from 192.168.0.1: icmp_req=16 ttl=64 time=109 ms
64 bytes from 192.168.0.1: icmp_req=17 ttl=64 time=29259 ms
64 bytes from 192.168.0.1: icmp_req=18 ttl=64 time=28250 ms
64 bytes from 192.168.0.1: icmp_req=19 ttl=64 time=27250 ms
64 bytes from 192.168.0.1: icmp_req=20 ttl=64 time=26251 ms

It looks like everything gets stuck for 15-40 seconds then the whole bunch of pings is sent at the same time. Sometimes it completely times out and gives destination host unreachable. For comparison, here's a sample from a different normal machine on the network:

kjellrs@proxima:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.269 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.269 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.260 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=0.260 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=64 time=0.263 ms

This is the problematic card:
kjellrs@balder:~$ lspci -v | grep thernet
04:05.0 Ethernet controller: Sundance Technology Inc / IC Plus Corp IP1000 Family Gigabit Ethernet (rev 41)
        Kernel driver in use: Sundance Technology IPG Triple-Speed Ethernet

I've tried now with both the maverick default kernel and 2.6.37-rc5 kernel (both 64 bit), same result. If I take the card up and down (ifup, ifdown) performance is restored for a little while, then it's back. I've tried changing cable, network card and router port but no luck. Help?

---

### Post by DeaDDingo_Inc on 2010-12-20
I have te same problem with the same network card,,, i post the problems in other forums but nobody response about that problem...

---

### Post by DeaDDingo_Inc on 2010-12-21
more tests...

leonardo@dummy:~$ ping 172.26.1.1
PING 172.26.1.1 (172.26.1.1) 56(84) bytes of data.
From 172.26.1.254 icmp_seq=1 Destination Host Unreachable
From 172.26.1.254 icmp_seq=2 Destination Host Unreachable
From 172.26.1.254 icmp_seq=3 Destination Host Unreachable
From 172.26.1.254 icmp_seq=4 Destination Host Unreachable
From 172.26.1.254 icmp_seq=5 Destination Host Unreachable
From 172.26.1.254 icmp_seq=6 Destination Host Unreachable
From 172.26.1.254 icmp_seq=7 Destination Host Unreachable
From 172.26.1.254 icmp_seq=8 Destination Host Unreachable
From 172.26.1.254 icmp_seq=9 Destination Host Unreachable
^C
--- 172.26.1.1 ping statistics ---
12 packets transmitted, 0 received, +9 errors, 100% packet loss, time 11062ms
pipe 3
leonardo@dummy:~$ sudo ifconfig eth1 up
[sudo] password for leonardo: 

Sorry, try again.
[sudo] password for leonardo: 
leonardo@dummy:~$ 
leonardo@dummy:~$ 
leonardo@dummy:~$ 
leonardo@dummy:~$ 
leonardo@dummy:~$ ping 172.26.1.1
PING 172.26.1.1 (172.26.1.1) 56(84) bytes of data.
From 172.26.1.254 icmp_seq=1 Destination Host Unreachable
From 172.26.1.254 icmp_seq=2 Destination Host Unreachable
From 172.26.1.254 icmp_seq=3 Destination Host Unreachable
^C
--- 172.26.1.1 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4022ms
pipe 3
leonardo@dummy:~$ sudo ifconfig vlan4 up
leonardo@dummy:~$ ping 172.26.1.1
PING 172.26.1.1 (172.26.1.1) 56(84) bytes of data.
From 172.26.1.254 icmp_seq=1 Destination Host Unreachable
From 172.26.1.254 icmp_seq=2 Destination Host Unreachable
From 172.26.1.254 icmp_seq=3 Destination Host Unreachable
^C
--- 172.26.1.1 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4022ms
pipe 3
leonardo@dummy:~$ sudo ifconfig vlan6 up
leonardo@dummy:~$ ping 172.26.1.1
PING 172.26.1.1 (172.26.1.1) 56(84) bytes of data.
From 172.26.1.254 icmp_seq=1 Destination Host Unreachable
From 172.26.1.254 icmp_seq=2 Destination Host Unreachable
From 172.26.1.254 icmp_seq=3 Destination Host Unreachable
^C
--- 172.26.1.1 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4023ms
pipe 3
leonardo@dummy:~$ sudo ifconfig eth1 up
leonardo@dummy:~$ sudo ifconfig eth1 up
leonardo@dummy:~$ ping 172.26.1.1
PING 172.26.1.1 (172.26.1.1) 56(84) bytes of data.
From 172.26.1.254 icmp_seq=1 Destination Host Unreachable
From 172.26.1.254 icmp_seq=2 Destination Host Unreachable
From 172.26.1.254 icmp_seq=3 Destination Host Unreachable
From 172.26.1.254 icmp_seq=4 Destination Host Unreachable
From 172.26.1.254 icmp_seq=5 Destination Host Unreachable
From 172.26.1.254 icmp_seq=6 Destination Host Unreachable
From 172.26.1.254 icmp_seq=7 Destination Host Unreachable
From 172.26.1.254 icmp_seq=8 Destination Host Unreachable
From 172.26.1.254 icmp_seq=9 Destination Host Unreachable
^C
--- 172.26.1.1 ping statistics ---
10 packets transmitted, 0 received, +9 errors, 100% packet loss, time 9045ms
pipe 3
leonardo@dummy:~$ route -n
Tabla de rutas IP del nÃºcleo
Destino         Pasarela        Genmask         Indic MÃ©tric Ref    Uso Interfaz
10.240.216.0    0.0.0.0         255.255.255.192 U     0      0        0 eth0
192.168.31.0    0.0.0.0         255.255.255.0   U     0      0        0 vlan4
172.26.0.0      0.0.0.0         255.255.0.0     U     0      0        0 vlan6
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.240.216.1    0.0.0.0         UG    100    0        0 eth0
leonardo@dummy:~$ ping 172.26.1.1
PING 172.26.1.1 (172.26.1.1) 56(84) bytes of data.
64 bytes from 172.26.1.1: icmp_req=1 ttl=255 time=11701 ms
64 bytes from 172.26.1.1: icmp_req=2 ttl=255 time=10695 ms
64 bytes from 172.26.1.1: icmp_req=3 ttl=255 time=9688 ms
64 bytes from 172.26.1.1: icmp_req=4 ttl=255 time=8681 ms
64 bytes from 172.26.1.1: icmp_req=5 ttl=255 time=7673 ms
64 bytes from 172.26.1.1: icmp_req=6 ttl=255 time=6666 ms
64 bytes from 172.26.1.1: icmp_req=7 ttl=255 time=5659 ms
64 bytes from 172.26.1.1: icmp_req=8 ttl=255 time=4651 ms
64 bytes from 172.26.1.1: icmp_req=9 ttl=255 time=3644 ms
^C
--- 172.26.1.1 ping statistics ---
31 packets transmitted, 9 received, 70% packet loss, time 30214ms
rtt min/avg/max/mdev = 3644.642/7673.636/11701.666/2600.573 ms, pipe 12
leonardo@dummy:~$ ping 172.26.1.1
PING 172.26.1.1 (172.26.1.1) 56(84) bytes of data.
64 bytes from 172.26.1.1: icmp_req=28 ttl=255 time=3348 ms
64 bytes from 172.26.1.1: icmp_req=29 ttl=255 time=2341 ms
64 bytes from 172.26.1.1: icmp_req=30 ttl=255 time=1334 ms
64 bytes from 172.26.1.1: icmp_req=31 ttl=255 time=335 ms
64 bytes from 172.26.1.1: icmp_req=80 ttl=255 time=11.9 ms
64 bytes from 172.26.1.1: icmp_req=32 ttl=255 time=48397 ms
64 bytes from 172.26.1.1: icmp_req=33 ttl=255 time=47389 ms
64 bytes from 172.26.1.1: icmp_req=34 ttl=255 time=46382 ms
64 bytes from 172.26.1.1: icmp_req=35 ttl=255 time=45374 ms
64 bytes from 172.26.1.1: icmp_req=36 ttl=255 time=44367 ms
64 bytes from 172.26.1.1: icmp_req=37 ttl=255 time=43360 ms
64 bytes from 172.26.1.1: icmp_req=38 ttl=255 time=42352 ms
64 bytes from 172.26.1.1: icmp_req=39 ttl=255 time=41345 ms
64 bytes from 172.26.1.1: icmp_req=40 ttl=255 time=40338 ms
64 bytes from 172.26.1.1: icmp_req=41 ttl=255 time=39331 ms
64 bytes from 172.26.1.1: icmp_req=42 ttl=255 time=38323 ms
64 bytes from 172.26.1.1: icmp_req=43 ttl=255 time=37316 ms
64 bytes from 172.26.1.1: icmp_req=44 ttl=255 time=36309 ms
64 bytes from 172.26.1.1: icmp_req=45 ttl=255 time=35301 ms
64 bytes from 172.26.1.1: icmp_req=46 ttl=255 time=34294 ms
64 bytes from 172.26.1.1: icmp_req=47 ttl=255 time=33287 ms
64 bytes from 172.26.1.1: icmp_req=48 ttl=255 time=32280 ms
64 bytes from 172.26.1.1: icmp_req=49 ttl=255 time=31272 ms
64 bytes from 172.26.1.1: icmp_req=50 ttl=255 time=30265 ms
64 bytes from 172.26.1.1: icmp_req=51 ttl=255 time=29258 ms
64 bytes from 172.26.1.1: icmp_req=52 ttl=255 time=28251 ms
64 bytes from 172.26.1.1: icmp_req=53 ttl=255 time=27243 ms
64 bytes from 172.26.1.1: icmp_req=54 ttl=255 time=26236 ms
64 bytes from 172.26.1.1: icmp_req=55 ttl=255 time=25229 ms
64 bytes from 172.26.1.1: icmp_req=56 ttl=255 time=24222 ms
64 bytes from 172.26.1.1: icmp_req=57 ttl=255 time=23214 ms
64 bytes from 172.26.1.1: icmp_req=58 ttl=255 time=22207 ms
64 bytes from 172.26.1.1: icmp_req=59 ttl=255 time=21200 ms
64 bytes from 172.26.1.1: icmp_req=60 ttl=255 time=20192 ms
64 bytes from 172.26.1.1: icmp_req=61 ttl=255 time=19185 ms
64 bytes from 172.26.1.1: icmp_req=62 ttl=255 time=18178 ms
64 bytes from 172.26.1.1: icmp_req=63 ttl=255 time=17170 ms
64 bytes from 172.26.1.1: icmp_req=64 ttl=255 time=16163 ms
64 bytes from 172.26.1.1: icmp_req=65 ttl=255 time=15156 ms
64 bytes from 172.26.1.1: icmp_req=66 ttl=255 time=14149 ms
64 bytes from 172.26.1.1: icmp_req=67 ttl=255 time=13141 ms
64 bytes from 172.26.1.1: icmp_req=68 ttl=255 time=12134 ms
64 bytes from 172.26.1.1: icmp_req=69 ttl=255 time=11127 ms
64 bytes from 172.26.1.1: icmp_req=70 ttl=255 time=10120 ms
64 bytes from 172.26.1.1: icmp_req=71 ttl=255 time=9112 ms
64 bytes from 172.26.1.1: icmp_req=72 ttl=255 time=8105 ms
64 bytes from 172.26.1.1: icmp_req=81 ttl=255 time=9174 ms
64 bytes from 172.26.1.1: icmp_req=82 ttl=255 time=8168 ms
64 bytes from 172.26.1.1: icmp_req=83 ttl=255 time=7161 ms
64 bytes from 172.26.1.1: icmp_req=84 ttl=255 time=6151 ms
64 bytes from 172.26.1.1: icmp_req=85 ttl=255 time=5152 ms
64 bytes from 172.26.1.1: icmp_req=86 ttl=255 time=4154 ms
64 bytes from 172.26.1.1: icmp_req=87 ttl=255 time=3155 ms
64 bytes from 172.26.1.1: icmp_req=88 ttl=255 time=2156 ms
64 bytes from 172.26.1.1: icmp_req=89 ttl=255 time=1157 ms
64 bytes from 172.26.1.1: icmp_req=90 ttl=255 time=158 ms
64 bytes from 172.26.1.1: icmp_req=91 ttl=255 time=3569 ms
64 bytes from 172.26.1.1: icmp_req=92 ttl=255 time=2561 ms
64 bytes from 172.26.1.1: icmp_req=93 ttl=255 time=1554 ms
64 bytes from 172.26.1.1: icmp_req=94 ttl=255 time=547 ms
^C
--- 172.26.1.1 ping statistics ---
95 packets transmitted, 60 received, 36% packet loss, time 94651ms
rtt min/avg/max/mdev = 11.946/20341.513/48397.380/15308.400 ms, pipe 49
leonardo@dummy:~$ ping 172.26.1.1
PING 172.26.1.1 (172.26.1.1) 56(84) bytes of data.
^C
--- 172.26.1.1 ping statistics ---
7 packets transmitted, 0 received, 100% packet loss, time 6030ms

leonardo@dummy:~$ ping 172.26.1.1
PING 172.26.1.1 (172.26.1.1) 56(84) bytes of data.
64 bytes from 172.26.1.1: icmp_req=1 ttl=255 time=7245 ms
64 bytes from 172.26.1.1: icmp_req=2 ttl=255 time=6245 ms
64 bytes from 172.26.1.1: icmp_req=3 ttl=255 time=5240 ms
64 bytes from 172.26.1.1: icmp_req=4 ttl=255 time=4232 ms
64 bytes from 172.26.1.1: icmp_req=5 ttl=255 time=3225 ms
64 bytes from 172.26.1.1: icmp_req=6 ttl=255 time=2226 ms
64 bytes from 172.26.1.1: icmp_req=7 ttl=255 time=1220 ms
64 bytes from 172.26.1.1: icmp_req=8 ttl=255 time=213 ms
64 bytes from 172.26.1.1: icmp_req=9 ttl=255 time=3092 ms
64 bytes from 172.26.1.1: icmp_req=10 ttl=255 time=2085 ms
64 bytes from 172.26.1.1: icmp_req=11 ttl=255 time=1078 ms
64 bytes from 172.26.1.1: icmp_req=12 ttl=255 time=70.7 ms
^C
--- 172.26.1.1 ping statistics ---
23 packets transmitted, 12 received, 47% packet loss, time 22064ms
rtt min/avg/max/mdev = 70.791/3014.730/7245.492/2232.243 ms, pipe 8
leonardo@dummy:~$ sudo ifconfig eth1 down
leonardo@dummy:~$ sudo ifconfig eth1 up
leonardo@dummy:~$ ping 172.26.1.1
PING 172.26.1.1 (172.26.1.1) 56(84) bytes of data.
From 172.26.1.254 icmp_seq=1 Destination Host Unreachable
From 172.26.1.254 icmp_seq=2 Destination Host Unreachable
From 172.26.1.254 icmp_seq=3 Destination Host Unreachable
From 172.26.1.254 icmp_seq=4 Destination Host Unreachable
From 172.26.1.254 icmp_seq=5 Destination Host Unreachable
From 172.26.1.254 icmp_seq=6 Destination Host Unreachable
From 172.26.1.254 icmp_seq=7 Destination Host Unreachable
From 172.26.1.254 icmp_seq=8 Destination Host Unreachable
From 172.26.1.254 icmp_seq=9 Destination Host Unreachable
From 172.26.1.254 icmp_seq=10 Destination Host Unreachable
From 172.26.1.254 icmp_seq=11 Destination Host Unreachable
From 172.26.1.254 icmp_seq=12 Destination Host Unreachable
From 172.26.1.254 icmp_seq=13 Destination Host Unreachable
From 172.26.1.254 icmp_seq=14 Destination Host Unreachable
From 172.26.1.254 icmp_seq=15 Destination Host Unreachable
From 172.26.1.254 icmp_seq=16 Destination Host Unreachable
From 172.26.1.254 icmp_seq=17 Destination Host Unreachable
From 172.26.1.254 icmp_seq=18 Destination Host Unreachable
From 172.26.1.254 icmp_seq=19 Destination Host Unreachable
From 172.26.1.254 icmp_seq=20 Destination Host Unreachable
From 172.26.1.254 icmp_seq=21 Destination Host Unreachable
From 172.26.1.254 icmp_seq=22 Destination Host Unreachable
From 172.26.1.254 icmp_seq=23 Destination Host Unreachable
From 172.26.1.254 icmp_seq=24 Destination Host Unreachable
From 172.26.1.254 icmp_seq=25 Destination Host Unreachable
From 172.26.1.254 icmp_seq=26 Destination Host Unreachable
From 172.26.1.254 icmp_seq=27 Destination Host Unreachable
From 172.26.1.254 icmp_seq=30 Destination Host Unreachable
^C
--- 172.26.1.1 ping statistics ---
31 packets transmitted, 0 received, +28 errors, 100% packet loss, time 30157ms
pipe 3
leonardo@dummy:~$ sudo ifconfig vlan6 down
leonardo@dummy:~$ sudo ifconfig vlan4 down
leonardo@dummy:~$ sudo ifconfig eth1 down
leonardo@dummy:~$ sudo ifconfig eth1 up
leonardo@dummy:~$ sudo ifconfig vlan4 up
leonardo@dummy:~$ sudo ifconfig vlan6 up
leonardo@dummy:~$ ping 172.26.1.1
PING 172.26.1.1 (172.26.1.1) 56(84) bytes of data.
64 bytes from 172.26.1.1: icmp_req=1 ttl=255 time=39.8 ms
64 bytes from 172.26.1.1: icmp_req=2 ttl=255 time=1.47 ms
64 bytes from 172.26.1.1: icmp_req=3 ttl=255 time=1.47 ms
64 bytes from 172.26.1.1: icmp_req=4 ttl=255 time=1.51 ms
64 bytes from 172.26.1.1: icmp_req=5 ttl=255 time=1.47 ms
64 bytes from 172.26.1.1: icmp_req=6 ttl=255 time=1.48 ms
64 bytes from 172.26.1.1: icmp_req=7 ttl=255 time=1.50 ms
64 bytes from 172.26.1.1: icmp_req=8 ttl=255 time=1.48 ms
64 bytes from 172.26.1.1: icmp_req=9 ttl=255 time=1.48 ms
64 bytes from 172.26.1.1: icmp_req=10 ttl=255 time=1.44 ms
^C
--- 172.26.1.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9014ms
rtt min/avg/max/mdev = 1.445/5.320/39.854/11.511 ms
leonardo@dummy:~$

---

### Post by DeaDDingo_Inc on 2010-12-21
I think in my case can resolve apparently, my machine had 2 network cards, both attached to the same switch, a port connected to an access port and another port connected to a port trunk, you may have generated some sort of loop and port have been blocking. As the access port in VLAN 1 was only delete it and move everything to a single card, configure a static ip on the card and add the other VLANs that already were using. I've been doing for most of the afternoon and has not fallen back into the network card.

---

### Post by DeaDDingo_Inc on 2010-12-22
Today, I have the problem again ... simply the ips in that I have configured vlans stop responding I have to go up and down the vlan to respond again ip

---

