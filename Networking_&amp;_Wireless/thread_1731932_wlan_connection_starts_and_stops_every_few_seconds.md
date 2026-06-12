---
title: "wlan connection starts and stops every few seconds"
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by fascinatedUser on 2011-04-17
Dear ubuntu friends,

I have a problem with my wlan connection. it works for few seconds, then stops for few seconds and then starts again (without interaction from my side). I run Ubuntu 10.4 Lucid. The issue started few days ago. Using ethernet, there is no problem.

The problem does not exist with other computers i have, there wifi and internet work continuously and flawless. 

It would be really great if you could help me resolve the issue...

I attached three pieces of info, which maybe help:

==================================== 
I ping my wlan router. one sees that connection to the wlan router starts and stops every few seconds... (of course, internet connection then behaves analogous)

> PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=1.30 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=1.21 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=1.46 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=1.45 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=1.91 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=1.46 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=1.46 ms
From 192.168.1.2 icmp_seq=38 Destination Host Unreachable
From 192.168.1.2 icmp_seq=39 Destination Host Unreachable
From 192.168.1.2 icmp_seq=40 Destination Host Unreachable
64 bytes from 192.168.1.1: icmp_seq=41 ttl=64 time=12.5 ms
64 bytes from 192.168.1.1: icmp_seq=42 ttl=64 time=1.25 ms
64 bytes from 192.168.1.1: icmp_seq=43 ttl=64 time=1.47 ms
64 bytes from 192.168.1.1: icmp_seq=44 ttl=64 time=1.45 ms
64 bytes from 192.168.1.1: icmp_seq=51 ttl=64 time=36.9 ms
64 bytes from 192.168.1.1: icmp_seq=52 ttl=64 time=1.29 ms
64 bytes from 192.168.1.1: icmp_seq=53 ttl=64 time=1.50 ms
64 bytes from 192.168.1.1: icmp_seq=54 ttl=64 time=1.48 ms
64 bytes from 192.168.1.1: icmp_seq=55 ttl=64 time=1.48 ms
64 bytes from 192.168.1.1: icmp_seq=56 ttl=64 time=2.25 ms
64 bytes from 192.168.1.1: icmp_seq=57 ttl=64 time=1.84 ms
64 bytes from 192.168.1.1: icmp_seq=58 ttl=64 time=1.48 ms
From 192.168.1.2 icmp_seq=87 Destination Host Unreachable
From 192.168.1.2 icmp_seq=88 Destination Host Unreachable
From 192.168.1.2 icmp_seq=89 Destination Host Unreachable
From 192.168.1.2 icmp_seq=90 Destination Host Unreachable
From 192.168.1.2 icmp_seq=91 Destination Host Unreachable
From 192.168.1.2 icmp_seq=92 Destination Host Unreachable
From 192.168.1.2 icmp_seq=94 Destination Host Unreachable
From 192.168.1.2 icmp_seq=95 Destination Host Unreachable
From 192.168.1.2 icmp_seq=96 Destination Host Unreachable
From 192.168.1.2 icmp_seq=98 Destination Host Unreachable
From 192.168.1.2 icmp_seq=99 Destination Host Unreachable
From 192.168.1.2 icmp_seq=100 Destination Host Unreachable
From 192.168.1.2 icmp_seq=101 Destination Host Unreachable
From 192.168.1.2 icmp_seq=102 Destination Host Unreachable
From 192.168.1.2 icmp_seq=103 Destination Host Unreachable
From 192.168.1.2 icmp_seq=105 Destination Host Unreachable
From 192.168.1.2 icmp_seq=106 Destination Host Unreachable
From 192.168.1.2 icmp_seq=107 Destination Host Unreachable
From 192.168.1.2 icmp_seq=108 Destination Host Unreachable
From 192.168.1.2 icmp_seq=109 Destination Host Unreachable
From 192.168.1.2 icmp_seq=110 Destination Host Unreachable
From 192.168.1.2 icmp_seq=112 Destination Host Unreachable
From 192.168.1.2 icmp_seq=113 Destination Host Unreachable
From 192.168.1.2 icmp_seq=114 Destination Host Unreachable
From 192.168.1.2 icmp_seq=115 Destination Host Unreachable
From 192.168.1.2 icmp_seq=116 Destination Host Unreachable
From 192.168.1.2 icmp_seq=117 Destination Host Unreachable
From 192.168.1.2 icmp_seq=119 Destination Host Unreachable
From 192.168.1.2 icmp_seq=120 Destination Host Unreachable
From 192.168.1.2 icmp_seq=121 Destination Host Unreachable
From 192.168.1.2 icmp_seq=123 Destination Host Unreachable
From 192.168.1.2 icmp_seq=124 Destination Host Unreachable
From 192.168.1.2 icmp_seq=125 Destination Host Unreachable
64 bytes from 192.168.1.1: icmp_seq=126 ttl=64 time=13.3 ms
64 bytes from 192.168.1.1: icmp_seq=127 ttl=64 time=1.27 ms
64 bytes from 192.168.1.1: icmp_seq=128 ttl=64 time=1.85 ms
64 bytes from 192.168.1.1: icmp_seq=129 ttl=64 time=1.45 ms
^C
--- 192.168.1.1 ping statistics ---
130 packets transmitted, 23 received, +36 errors, 82% packet loss, time 129154ms
rtt min/avg/max/mdev = 1.214/4.050/36.934/7.712 ms, pipe 4
===============================================================

output of ifconfig:

> eth0      Link encap:Ethernet  HWaddr 00:24:81:b0:26:43  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:d8400000-d8420000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:491 errors:0 dropped:0 overruns:0 frame:0
          TX packets:491 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43112 (43.1 KB)  TX bytes:43112 (43.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:6a:11:cf:68  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:6aff:fe11:cf68/64 Scope:Link                                                                                                          
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:94322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78038 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:104533609 (104.5 MB)  TX bytes:12416753 (12.4 MB)
===============================================================

output of 'lshw -C network'


> WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:24:81:b0:26:43
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=1.8-3 latency=0 multicast=yes
       resources: irq:30 memory:d8400000-d841ffff memory:d8424000-d8424fff ioport:80e0(size=32)
  *-network
       description: Wireless interface
       product: Wireless WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6a:11:cf:68
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.2 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:d8100000-d8101fff

===============================================================

---

### Post by uncaspi on 2011-04-17
Try to turn off power save mode and increase transmitting power.

sudo iwconfig wlan0 power off txpower 20

---

### Post by fascinatedUser on 2011-04-18
Dear Uncaspi,

thank you for your quick answer. 

unfortunately, your hint did not help. the connection did not get better.

the output was 
> sudo iwconfig wlan0 power off txpower 20
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Invalid argument.

the output of "iwconfig" is
> wconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"ASUS"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 48:5B:39:BD:09:B4   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-18 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


Further pieces of information, which maybe help: 
[LIST]
[*] The problem does not exist at work. 
[*] my wlan router is "asus RT-NT13U" 
[/LIST]

regards, f.U.

---

### Post by fascinatedUser on 2011-04-20
no one? any idea?
:( :( :(

---

