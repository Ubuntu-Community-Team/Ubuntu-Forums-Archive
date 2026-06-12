---
title: "Unable to ping on network..."
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by AceVenturaX on 2011-01-11
I have ubuntu 10.4 running on both my desktop and laptop. Both machines are connected to the router in wireless mode with Wifi. 
I can access internet from both machines without any issues, however I cant ping one machine from another. (and vice versa)

I have setup static IP addresses for both machines... 

Route on laptop shows :

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.222   0.0.0.0         UG    0      0        0 wlan0

```Following is the result of pings :


```

zzzzzz@venture-laptop:/home/venture# ping 192.168.1.100
PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
From 192.168.1.101 icmp_seq=1 Destination Host Unreachable
From 192.168.1.101 icmp_seq=2 Destination Host Unreachable
From 192.168.1.101 icmp_seq=3 Destination Host Unreachable
From 192.168.1.101 icmp_seq=4 Destination Host Unreachable
From 192.168.1.101 icmp_seq=5 Destination Host Unreachable
From 192.168.1.101 icmp_seq=6 Destination Host Unreachable
^C
--- 192.168.1.100 ping statistics ---
8 packets transmitted, 0 received, +6 errors, 100% packet loss, time 7039ms
, pipe 3
zzzzz@venture-laptop:/home/venture# ping 192.168.1.222
PING 192.168.1.222 (192.168.1.222) 56(84) bytes of data.
64 bytes from 192.168.1.222: icmp_seq=1 ttl=254 time=1.67 ms
64 bytes from 192.168.1.222: icmp_seq=2 ttl=254 time=1.21 ms
64 bytes from 192.168.1.222: icmp_seq=3 ttl=254 time=1.24 ms
64 bytes from 192.168.1.222: icmp_seq=4 ttl=254 time=1.03 ms
^C
--- 192.168.1.222 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 1.038/1.291/1.671/0.234 ms
zzzzz@venture-laptop:/home/venture# 


```100 is the desktop machine and 222 is the router...
Any advise on whats going wrong here ?:confused:

---

### Post by PatchesTheCaveman on 2011-01-12
Is your firewall configured to block ICMP/ping requests?

Try following the instructions to enable it in this help article:
[https://help.ubuntu.com/community/UFW#Enable PING](https://help.ubuntu.com/community/UFW#Enable PING)

---

### Post by AceVenturaX on 2011-01-12
I do not have any firewall on the network. The built in firewall for router has also been disabled. And UFW has also been disabled. Still facing the same issue...


```
venture@venture-desktop:~$ sudo ufw status
Status: inactive
```


Any hope to get to the bottom of this ?

---

### Post by AceVenturaX on 2011-01-15
BUMP !!!


Anybody there ???


I have lost hope and am thinking of going back to window$.

Both machines have IP , can ping the router, and access internet, are on the same network
but ABSOLUTELY refuse to ping each other.

Machine 1 NMAP

```
Starting Nmap 5.00 ( http://nmap.org ) at 2011-01-15 20:36 IST
Interesting ports on 192.168.1.101:
Not shown: 995 closed ports
PORT     STATE SERVICE
53/tcp   open  domain
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
2049/tcp open  nfs

Interesting ports on 192.168.1.222:
Not shown: 997 closed ports
PORT   STATE SERVICE
21/tcp open  ftp
23/tcp open  telnet
80/tcp open  http

Nmap done: 256 IP addresses (2 hosts up) scanned in 32.63 seconds
```


Machine 2 NMAP

```
Starting Nmap 5.00 ( http://nmap.org ) at 2011-01-15 20:39 IST
Interesting ports on 192.168.1.100:
Not shown: 996 closed ports
PORT     STATE SERVICE
53/tcp   open  domain
80/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds

Interesting ports on 192.168.1.222:
Not shown: 997 closed ports
PORT   STATE SERVICE
21/tcp open  ftp
23/tcp open  telnet
80/tcp open  http

Nmap done: 256 IP addresses (2 hosts up) scanned in 32.63 seconds
```

ANYBODY .... any clue ???

---

### Post by Iowan on 2011-01-15
Windows machines can ping each other through the router?

---

