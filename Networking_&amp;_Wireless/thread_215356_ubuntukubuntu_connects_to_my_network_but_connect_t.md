---
title: "ubuntu/kubuntu connects to my network but connect to net"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by maddbaron on 2006-07-13
My internet company verizon messed up my account so I wasnt able to connect to my network for the past week. I was using another network in my home. So now Verizon decides to fix my connection and I can connect via desktop (xp) and wirelessly via xp but when I boot into Kubuntu or Ubuntu my network gets picked up even has signal strength but no browsers or messengers work. firestarter works and picks up the network tho. Now when I set up my ubuntu months back i had to manually enter my dns info. I did that again just now b/c my dns changed but i still can't connect. is there a way to fix this in kubuntu? i want to connect wirelessly. I have my ppp ip and my main dns and sub dns info ready.

can someone help me and tell me what to input and where to do it?

> 
sudo ifup eth1

> ifup: interface eth1 already configured

The orange wireless connect light began flashing.

> output of iwconfig and ifconfig
Also run ping -c3 google.com

> lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11g ESSID:"05B408580701"
Mode:Managed Frequency:2.437 GHz Access Point: 00:12:0E:10:19:B0
Bit Rate:18 Mb/s Tx-Power:25 dBm
RTS thr:2347 B Fragment thr:2346 B
Power Managementff
Link Quality:100/100 Signal level:-75 dBm Noise level:-256 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0 no wireless extensions.

maddbaron@ubuntu:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:C0:9F:A3:21:48
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:169 Base address:0x1800

eth1 Link encap:Ethernet HWaddr 00:0E:9B:CD:84:0B
inet addr:192.168.1.41 Bcast:255.255.255.255 Mask:255.255.255.0
inet6 addr: fe80::20e:9bff:fecd:840b/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:33 errors:0 dropped:0 overruns:0 frame:0
TX packets:192 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:2263 (2.2 KiB) TX bytes:16010 (15.6 KiB)
Interrupt:217 Memory:e2000000-e2002000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:5 errors:0 dropped:0 overruns:0 frame:0
TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:256 (256.0 b) TX bytes:256 (256.0 b)

maddbaron@ubuntu:~$ ping -c3.google.com
Usage: ping [-LRUbdfnqrvVaA] [-c count] [-i interval] [-w deadline]
[-p pattern] [-s packetsize] [-t ttl] [-I interface or address]
[-M mtu discovery hint] [-S sndbuf]
[ -T timestamp option ] [ -Q tos ] [hop1 ...] destination

I can connect and use the net via another network in my home but that ip address didnt change but then again i never entered it. the OS just picked it up. 

so I am assuming the problem is the ip address i entered can't be found b/c when verizon reconnected me my ip address changed also.

when i go into firestarter it shows the ip i believe for my old ip i entered the new dns' and still didnt work altho it still connected and when i restarted i got kernal panic on the street.

can someone help me fix this so it can pick up my network?  and there a way to view open networks in kubuntu and ubuntu so i can switch if need be?

---

