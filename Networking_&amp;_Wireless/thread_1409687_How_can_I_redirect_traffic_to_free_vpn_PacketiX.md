---
title: "How can I redirect traffic to free vpn PacketiX?"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by argothian on 2010-02-17
Hi, I am studying in China now and because of censorship, I was trying to find some free VPN service for access restricted pages. I found some working programs for win XP, but nothing works under Linux (TOR was too slow and now it is blocked).
I was using program PacketiX under win, and it has also Linux version without GUI, but i was not able to make it work, because I dont know, how can I make firefox to connect through the VPN service.

I downloaded the client here
[http://www.packetix.net/en/secure/install/](http://www.packetix.net/en/secure/install/)

I was able to make it work with this guide
[http://wan.pengganas.net/entry/packetix-net-vpn-installation-on-linux/](http://wan.pengganas.net/entry/packetix-net-vpn-installation-on-linux/)

But i dont know, how to adjust routing table so I can connect to the internet through the VPN service. 

ifconfig
```
ath0      Link encap:Ethernet  HWaddr 00:05:4e:4d:c5:5f  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:52603 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52458 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16061046 (16.0 MB)  TX bytes:5034925 (5.0 MB)

eth0      Link encap:Ethernet  HWaddr 00:0d:60:5e:8d:de  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:551 errors:0 dropped:0 overruns:0 frame:0
          TX packets:551 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:32574 (32.5 KB)  TX bytes:32574 (32.5 KB)

vpn_0     Link encap:Ethernet  HWaddr 00:ac:cb:c1:eb:43  
          inet addr:10.4.99.180  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::2ac:cbff:fec1:eb43/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28077 errors:0 dropped:0 overruns:0 frame:0
          TX packets:138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:2139202 (2.1 MB)  TX bytes:8969 (8.9 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-05-4E-4D-C5-5F-62-34-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:279171 errors:0 dropped:0 overruns:0 frame:81974
          TX packets:53348 errors:433 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:50640305 (50.6 MB)  TX bytes:7295611 (7.2 MB)
          Interrupt:11 

```route (I can connect to the internet)
```
192.168.1.0     *               255.255.255.0   U     2      0        0 ath0
link-local      *               255.255.0.0     U     1000   0        0 ath0
10.0.0.0        *               255.0.0.0       U     0      0        0 vpn_0
default         localhost       0.0.0.0         UG    0      0        0 ath0
```route (I cannot connect to the internet) -> after 'dhclient vpn_0'
```
192.168.1.0     *               255.255.255.0   U     2      0        0 ath0
10.0.0.0        *               255.0.0.0       U     0      0        0 vpn_0
default         10.0.0.1        0.0.0.0         UG    0      0        0 vpn_0
default         192.168.1.1     0.0.0.0         UG    0      0        0 ath0
```My computer is connected to wireless router. I have chinese ISP, I am using PPPoE
I have Xubuntu 8.10
Thanks for help and sorry for my English :-)

---

### Post by Tsu jan on 2011-01-17
It may be too late to reply but I recently had the same issue with the same route table. To fix the problem, I didn't use the commands "route del default" and "route add default dev vpn_0" but just did:

dhclient vpn_0

and then:

ip route add 192.168.1.0/24 via 10.0.0.1

After that, the connection was established :D

---

