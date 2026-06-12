---
title: "Connection not working over cisco VPN"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by itsmesanju on 2011-01-12
Hi Guys,

I am using ubuntu 10.10 and facing problem with cisco VPN connection. VPN connection is getting successful but not able to connect to destination servers.


BEFORE CONNECTION:

xyz@ggn2un05:sudo route -n
[COLOR="Red"]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.248.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.248.1   0.0.0.0         UG    0      0        0 eth0[/COLOR]
xyz@ggn2un05:

xyz@ggn2un05:sudo ifconfig -a
[COLOR="Red"]eth0      Link encap:Ethernet  HWaddr 00:1c:c4:1d:90:54
          inet addr:192.168.248.146  Bcast:192.168.248.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c4ff:fe1d:9054/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1560 errors:0 dropped:0 overruns:0 frame:0
          TX packets:142 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:240045 (240.0 KB)  TX bytes:23588 (23.5 KB)
          Interrupt:19

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2144 (2.1 KB)  TX bytes:2144 (2.1 KB)
[/COLOR]
xyz@ggn2un05:


xxx@ggns2un053: ~$ sudo vpnclient connect xxx
[COLOR="Blue"]Cisco Systems VPN Client Version 4.8.01 (0640)
Copyright (C) 1998-2007 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 09:00:03 UTC 2010 i686
Config file directory: /etc/opt/cisco-vpnclient

Initializing the VPN connection.
Contacting the gateway at XX.XX.XX.XX
User Authentication for XXX...

Enter Username and Password.

Username [XXX@XXX]:
Password []:
Authenticating user.
Negotiating security policies.
Securing communication channel.

Do you wish to continue? (y/n): y
Your VPN connection is secure.

VPN tunnel information.
Client address: 10.0.45.192
Server address: 80.125.165.164
Encryption: 168-bit 3-DES
Authentication: HMAC-MD5
IP Compression: None
NAT passthrough is active on port UDP 10000
Local LAN Access is disabled
[/COLOR]

And after that when I am trying to connect to one of the VPN network's server, its not getting connected.

The route and ifconfig output after VPN connection are provided below.

[COLOR="Red"]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.4.143.245    10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.17.225.249   10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.17.225.252   10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
164.128.41.75   10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.4.139.199    10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.4.139.200    10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.4.139.205    10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.104.9.10     10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.153.151.117  10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
80.125.165.164  192.168.248.1   255.255.255.255 UGH   0      0        0 eth0
10.153.151.116  10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.18.1.48      10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.18.1.79      10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.18.1.77      10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.193.130.20   10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.153.130.165  10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.104.7.42     10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.104.7.38     10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.4.241.106    10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.56.209.23    10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.193.151.116  10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.193.151.117  10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.193.130.216  10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.4.136.85     10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.4.135.22     10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.102.5.108    10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.4.135.5      10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.4.134.5      10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.4.137.9      10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.4.142.29     10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.4.142.28     10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.102.9.66     10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.4.142.21     10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.4.142.20     10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.102.9.82     10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.193.130.165  10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.153.130.20   10.0.45.192     255.255.255.255 UGH   0      0        0 cipsec0
10.4.136.88     10.0.45.192     255.255.255.252 UG    0      0        0 cipsec0
10.193.131.116  10.0.45.192     255.255.255.252 UG    0      0        0 cipsec0
10.0.34.0       10.0.45.192     255.255.255.248 UG    0      0        0 cipsec0
10.56.209.56    10.0.45.192     255.255.255.248 UG    0      0        0 cipsec0
10.153.130.144  10.0.45.192     255.255.255.240 UG    0      0        0 cipsec0
10.153.131.144  10.0.45.192     255.255.255.240 UG    0      0        0 cipsec0
10.119.86.128   10.0.45.192     255.255.255.240 UG    0      0        0 cipsec0
10.153.130.80   10.0.45.192     255.255.255.240 UG    0      0        0 cipsec0
10.117.23.0     10.0.45.192     255.255.255.240 UG    0      0        0 cipsec0
10.193.131.144  10.0.45.192     255.255.255.240 UG    0      0        0 cipsec0
10.0.34.112     10.0.45.192     255.255.255.240 UG    0      0        0 cipsec0
10.4.131.128    10.0.45.192     255.255.255.224 UG    0      0        0 cipsec0
10.4.131.0      10.0.45.192     255.255.255.224 UG    0      0        0 cipsec0
10.4.133.0      10.0.45.192     255.255.255.224 UG    0      0        0 cipsec0
10.4.250.160    10.0.45.192     255.255.255.224 UG    0      0        0 cipsec0
10.4.132.128    10.0.45.192     255.255.255.224 UG    0      0        0 cipsec0
10.117.22.192   10.0.45.192     255.255.255.224 UG    0      0        0 cipsec0
10.4.132.0      10.0.45.192     255.255.255.224 UG    0      0        0 cipsec0
10.153.150.0    10.0.45.192     255.255.255.192 UG    0      0        0 cipsec0
10.0.43.128     10.0.45.192     255.255.255.192 UG    0      0        0 cipsec0
10.153.140.0    10.0.45.192     255.255.255.0   UG    0      0        0 cipsec0
10.153.137.0    10.0.45.192     255.255.255.0   UG    0      0        0 cipsec0
10.0.45.0       0.0.0.0         255.255.255.0   U     0      0        0 cipsec0
192.168.248.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0
10.56.0.0       10.0.45.192     255.255.255.0   UG    0      0        0 cipsec0
10.153.192.0    10.0.45.192     255.255.255.0   UG    0      0        0 cipsec0
10.130.0.0      10.0.45.192     255.255.0.0     UG    0      0        0 cipsec0
10.87.0.0       10.0.45.192     255.255.0.0     UG    0      0        0 cipsec0
10.88.0.0       10.0.45.192     255.255.0.0     UG    0      0        0 cipsec0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.248.1   0.0.0.0         UG    0      0        0 eth0[/COLOR]

AND

[COLOR="red"]cipsec0   Link encap:Ethernet  HWaddr 00:0b:fc:f8:01:8f
          inet addr:10.0.45.192  Mask:255.255.255.0
          inet6 addr: fe80::20b:fcff:fef8:18f/64 Scope:Link
          UP RUNNING NOARP  MTU:1356  Metric:1
          RX packets:0 errors:0 dropped:3 overruns:0 frame:0
          TX packets:0 errors:0 dropped:25 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1c:c4:1d:90:54
          inet addr:192.168.248.146  Bcast:192.168.248.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c4ff:fe1d:9054/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2345 errors:0 dropped:0 overruns:0 frame:0
          TX packets:312 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:351815 (351.8 KB)  TX bytes:55879 (55.8 KB)
          Interrupt:19

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:75 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:14172 (14.1 KB)  TX bytes:14172 (14.1 KB)[/COLOR]

I also tried to add default gw to the the IP which is assigned to my VPN connection but still access to VPN machines not working. Can someone please give me a clue to correct this?

---

### Post by itsmesanju on 2011-01-12
Alternatively, I have also tried vpnc but the end result is same. Whereas If i use WINDOWS based Cisco vpn client, its working perfectly.

---

