---
title: "Ubuntu 10.4 reconnecting several times per minute on wired connection"
date: 2012-02-24
forum: Networking &amp; Wireless
---

### Post by matismasters on 2012-02-24
Hi everyone, I have installed Ubuntu 10.4 on my desktop PC, via the Wubi installation. Everything works perfectly smooth, but the internet connection. As I'm surfing the web, or using git, or IRC, the connection is lost and engage over and over again, several times per minute, 1 of 3 or 5 requests gets to work properly.

I asked in the IRC Channel but anyone could help me, so I'm trying here. I'll paste the information about my system right here so you could have a better understanding of the problem.

Also In windows the internet connection works perfectly, without problem at all, so same cable, same router, and everything.

To configure I use the gnome applet form the top right of the screen. I never touched config/interfaces file or something like that I think is called.

```
matis@ubuntu:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 14:da:e9:15:44:92 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.2/24 brd 192.168.1.255 scope global eth0
    inet6 fe80::16da:e9ff:fe15:4492/64 scope link 
       valid_lft forever preferred_lft forever

```
IP ROUTE SHOW TABLE ALL
```
matis@ubuntu:~/$ ip route show table all
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.2  metric 1 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.1.1 dev eth0  proto static 
broadcast 192.168.1.0 dev eth0  table local  proto kernel  scope link  src 192.168.1.2 
broadcast 127.255.255.255 dev lo  table local  proto kernel  scope link  src 127.0.0.1 
local 192.168.1.2 dev eth0  table local  proto kernel  scope host  src 192.168.1.2 
broadcast 192.168.1.255 dev eth0  table local  proto kernel  scope link  src 192.168.1.2 
broadcast 127.0.0.0 dev lo  table local  proto kernel  scope link  src 127.0.0.1 
local 127.0.0.1 dev lo  table local  proto kernel  scope host  src 127.0.0.1 
local 127.0.0.0/8 dev lo  table local  proto kernel  scope host  src 127.0.0.1 
fe80::/64 dev eth0  proto kernel  metric 256  mtu 1500 advmss 1440 hoplimit 4294967295
unreachable default dev lo  table unspec  proto kernel  metric -1  error -101 hoplimit 255
local ::1 via :: dev lo  table local  proto none  metric 0  mtu 16436 advmss 16376 hoplimit 4294967295
local fe80::16da:e9ff:fe15:4492 via :: dev lo  table local  proto none  metric 0  mtu 16436 advmss 16376 hoplimit 4294967295
ff00::/8 dev eth0  table local  metric 256  mtu 1500 advmss 1440 hoplimit 4294967295
unreachable default dev lo  table unspec  proto kernel  metric -1  error -101 hoplimit 255

```
IP RULE
```

matis@ubuntu:~/$ ip rule
0:  from all lookup local 
32766:  from all lookup main 
32767:  from all lookup default 
matis@ubuntu:~/projects/jdjunkies$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```
TAIL /VAR/LOG/MESSAGES
```
matis@ubuntu:~/$ tail /var/log/messages
Feb 24 10:06:47 ubuntu kernel: [ 4765.834152] r8169: eth0: link up
Feb 24 10:06:57 ubuntu kernel: [ 4776.220206] r8169: eth0: link up
Feb 24 10:07:08 ubuntu kernel: [ 4787.640439] r8169: eth0: link up
Feb 24 10:07:29 ubuntu kernel: [ 4808.000214] r8169: eth0: link up
Feb 24 10:08:14 ubuntu kernel: [ 4853.571719] r8169: eth0: link up
Feb 24 10:08:30 ubuntu kernel: [ 4869.310131] r8169: eth0: link up
Feb 24 10:08:39 ubuntu kernel: [ 4878.660178] r8169: eth0: link up
Feb 24 10:08:42 ubuntu kernel: [ 4881.381243] r8169: eth0: link up
Feb 24 10:10:15 ubuntu kernel: [ 4974.540124] r8169: eth0: link up
Feb 24 10:12:18 ubuntu kernel: [ 5096.902926] r8169: eth0: link up

```
PING GOOGLE.COM
```

matis@ubuntu:~/projects/jdjunkies$ ping google.com
PING google.com (74.125.93.100) 56(84) bytes of data.
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=1 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=2 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=3 ttl=53 time=172 ms
64 bytes from 74.125.93.100: icmp_seq=4 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=56 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=57 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=58 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=59 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=60 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=61 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=62 ttl=53 time=175 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=67 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=68 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=69 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=70 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=71 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=72 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=73 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=78 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=79 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=80 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=81 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=82 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=83 ttl=53 time=174 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=84 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=85 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=86 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=87 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=88 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=89 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=90 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=98 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=99 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=100 ttl=53 time=174 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=101 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=102 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=103 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=104 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=105 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=106 ttl=53 time=194 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=107 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=108 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=109 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=110 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=111 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=112 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=113 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=114 ttl=53 time=171 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=115 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=116 ttl=53 time=175 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=117 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=144 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=145 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=146 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=147 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=148 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=149 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=150 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=151 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=152 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=153 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=154 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=155 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=156 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=160 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=161 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=162 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=163 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=164 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=165 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=166 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=167 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=168 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=169 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=170 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=172 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=173 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=174 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=175 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=176 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=177 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=178 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=179 ttl=53 time=180 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=180 ttl=53 time=185 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=181 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=182 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=183 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=184 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=185 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=186 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=187 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=188 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=189 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=190 ttl=53 time=173 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=191 ttl=53 time=172 ms
From ubuntu (192.168.1.2) icmp_seq=262 Destination Host Unreachable
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=263 ttl=53 time=175 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=264 ttl=53 time=172 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=265 ttl=53 time=174 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=266 ttl=53 time=175 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=267 ttl=53 time=175 ms
64 bytes from qw-in-f100.1e100.net (74.125.93.100): icmp_seq=268 ttl=53 time=172 ms

```

As you can see in there, when the Unreachable is return is like everytime I got dc and reconnnected back again, but the trobule doesn't seems to be in the response as its always the same when the connection is stablished, but the problem seems to be with the connection itself, I don't know

LSPCI
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1705
00:02.0 PCI bridge: Advanced Micro Devices [AMD] Device 1707
00:10.0 USB Controller: Advanced Micro Devices [AMD] Device 7812 (rev 03)
00:10.1 USB Controller: Advanced Micro Devices [AMD] Device 7812 (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Device 7800 (rev 40)
00:12.0 USB Controller: Advanced Micro Devices [AMD] Device 7807 (rev 11)
00:12.2 USB Controller: Advanced Micro Devices [AMD] Device 7808 (rev 11)
00:13.0 USB Controller: Advanced Micro Devices [AMD] Device 7807 (rev 11)
00:13.2 USB Controller: Advanced Micro Devices [AMD] Device 7808 (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Device 780b (rev 13)
00:14.1 IDE interface: Advanced Micro Devices [AMD] Device 780c
00:14.2 Audio device: Advanced Micro Devices [AMD] Device 780d (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Device 780e (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Device 780f (rev 40)
00:14.5 USB Controller: Advanced Micro Devices [AMD] Device 7809 (rev 11)
00:15.0 PCI bridge: Advanced Micro Devices [AMD] Device 43a0
00:15.1 PCI bridge: Advanced Micro Devices [AMD] Device 43a1
00:18.0 Host bridge: Advanced Micro Devices [AMD] Device 1700 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Device 1701
00:18.2 Host bridge: Advanced Micro Devices [AMD] Device 1702
00:18.3 Host bridge: Advanced Micro Devices [AMD] Device 1703
00:18.4 Host bridge: Advanced Micro Devices [AMD] Device 1704
00:18.5 Host bridge: Advanced Micro Devices [AMD] Device 1718
00:18.6 Host bridge: Advanced Micro Devices [AMD] Device 1716
00:18.7 Host bridge: Advanced Micro Devices [AMD] Device 1719
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6759
01:00.1 Audio device: ATI Technologies Inc Device aa90
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

```

IFCONFIG ETH0
```
eth0      Link encap:Ethernet  direcciÃ³nHW 14:da:e9:15:44:92  
          Direc. inet:192.168.1.2  Difus.:192.168.1.255  MÃ¡sc:255.255.255.0
          DirecciÃ³n inet6: fe80::16da:e9ff:fe15:4492/64 Alcance:Enlace
          ACTIVO DIFUSIÃ&#65533;N FUNCIONANDO MULTICAST  MTU:1500  MÃ©trica:1
          Paquetes RX:33483 errores:0 perdidos:33483 overruns:0 frame:33483
          Paquetes TX:38563 errores:0 perdidos:343 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:25634340 (25.6 MB)  TX bytes:5867389 (5.8 MB)
          InterrupciÃ³n:27 DirecciÃ³n base: 0x4000 
```

---

### Post by roelforg on 2012-02-24
Check the cable.
Probably faulty.

---

### Post by matismasters on 2012-02-25
Is not the cable, it works perfectly fine in windows in the same desktop pc, with the same cable, and router.

---

### Post by roelforg on 2012-02-25
Could you do me a favor and translate the output's from your first post to english?
It's riddled with other languages and characters my firefox can't render.

---

### Post by matismasters on 2012-02-25
> **matismasters said:**
> 
IFCONFIG ETH0
```
eth0      Link encap:Ethernet  direcciÃ³nHW 14:da:e9:15:44:92  
          Adress. inet:192.168.1.2  broadcast.:192.168.1.255  Ma¡sc:255.255.255.0
          Adress inet6: fe80::16da:e9ff:fe15:4492/64 Alcance:Enlace
          ACTIVE DIFUSION WORKING MULTICAST  MTU:1500  metric:1
          Packages RX:33483 errors:0 lost:33483 overruns:0 frame:33483
          Packages TX:38563 errors:0 lost:343 overruns:0 carrier:0
          colitions:0 long.queue TX:1000 
          Bytes RX:25634340 (25.6 MB)  TX bytes:5867389 (5.8 MB)
          Interuption:27 Address base: 0x4000 
```

That is the only one that neede translation, I trnslated word by word, not pretty sure if its ok.

---

