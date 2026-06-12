---
title: "Can't connect Ubuntu desktop to Ubuntu server in Virtualbox"
date: 2012-02-07
forum: Networking &amp; Wireless
---

### Post by AlanQ on 2012-02-07
I'm trying to ping and SSH
from
an Ubuntu desktop (10.04 64bit)
to
an Ubuntu server (10.04 64bit) running in Virtualbox (4.1.8) on the desktop

Ultimately I wish to use the server for web site testing, etc.
Sadly, I can't even ping it :s

I have searched this and other forums: unfortunately, although I'm not a Linux newb, networking confuses me so much that I might have seen the answer and not recognised it :(

------

VirtualBox:

File > Preferences > Network
Host Only Networks: [FONT="Courier New"]vboxnet0[/FONT]
Adapter
IPv4 address: [FONT="Courier New"]10.0.2.1[/FONT]
IPv4 network mask: [FONT="Courier New"]255.255.255.0[/FONT]
DHCP Server
Not Enabled

Ubuntu Server Settings > Network
Adapter 1
Attached to: NAT
Cable connected
No port forwarding
Adapter 2
Attached to: Host-only Adapter
Name: [FONT="Courier New"]vboxnet0[/FONT]
Promiscuous mode: Deny
Cable connected

------

Server:
[after login] System information...
IP address for eth0: [FONT="Courier New"]10.0.2.15[/FONT]

------

Desktop:

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr ...
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr ...
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:43ff:fe00:1031/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62556 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60322 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44033838 (44.0 MB)  TX bytes:5396425 (5.3 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6804 (6.8 KB)  TX bytes:6804 (6.8 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          inet addr:10.0.2.1  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::800:27ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.2.0        0.0.0.0         255.255.255.0   U     0      0        0 vboxnet0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
```

------

I can ping VirtualBox:
```
$ ping 10.0.2.1
PING 10.0.2.1 (10.0.2.1) 56(84) bytes of data.
64 bytes from 10.0.2.1: icmp_seq=1 ttl=64 time=0.092 ms
64 bytes from 10.0.2.1: icmp_seq=2 ttl=64 time=0.074 ms
64 bytes from 10.0.2.1: icmp_seq=3 ttl=64 time=0.071 ms
^C
--- 10.0.2.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 0.071/0.079/0.092/0.009 ms
```


I cannot ping the server:
```
$ ping 10.0.2.15
PING 10.0.2.15 (10.0.2.15) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
^C
--- 10.0.2.15 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2008ms

```
------

ssh:

```
$ ssh 10.0.2.1
ssh: connect to host 10.0.2.1 port 22: Connection refused
```

```
$ ssh 10.0.2.15
^C
```

------

---

