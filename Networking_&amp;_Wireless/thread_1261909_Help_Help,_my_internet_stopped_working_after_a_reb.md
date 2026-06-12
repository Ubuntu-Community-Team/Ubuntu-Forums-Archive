---
title: "Help Help, my internet stopped working after a reboot"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by Rocky1980 on 2009-09-09
Hi all,

I am in need of some help, I updated some files today and rebooted, however after the reboot I am no longer connect to the next. I connect though a wired connection to my router. I run a dual boot with Xp, so I booted that upand it works fine.  I then treid a live CD and agian I connected to the net ok.I am running Ubutnu 8.10

I have tried the following commands in termainal in both my main install and live CD. 

_Main installed (the broken one)_

**ping 195.76.187.83**
PING 195.76.187.83 (195.76.187.83) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

**ifconfig eth0**
eth0      Link encap:Ethernet  HWaddr 00:50:8d:91:fe:6e  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe91:fe6e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4656 (4.6 KB)  TX bytes:1184 (1.1 KB)
          Interrupt:23 Base address:0x4000 
**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:50:8d:91:fe:6e  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe91:fe6e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2896 (2.8 KB)  TX bytes:1184 (1.1 KB)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

_Live CD_

**ping 195.76.187.83**
PING 195.76.187.83 (195.76.187.83) 56(84) bytes of data.
64 bytes from 195.76.187.83: icmp_seq=1 ttl=113 time=78.9 ms
64 bytes from 195.76.187.83: icmp_seq=2 ttl=113 time=73.0 ms
64 bytes from 195.76.187.83: icmp_seq=3 ttl=113 time=73.7 ms
64 bytes from 195.76.187.83: icmp_seq=4 ttl=113 time=73.1 ms
64 bytes from 195.76.187.83: icmp_seq=5 ttl=113 time=71.3 ms
64 bytes from 195.76.187.83: icmp_seq=6 ttl=113 time=73.0 ms
64 bytes from 195.76.187.83: icmp_seq=7 ttl=113 time=70.1 ms




**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:50:8d:91:fe:6e  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe91:fe6e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14444 (14.1 KB)  TX bytes:12517 (12.2 KB)
          Interrupt:18 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7086 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7086 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:354300 (345.9 KB)  TX bytes:354300 (345.9 KB)



**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:50:8d:91:fe:6e  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe91:fe6e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14444 (14.1 KB)  TX bytes:12517 (12.2 KB)
          Interrupt:18 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7086 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7086 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:354300 (345.9 KB)  TX bytes:354300 (345.9 KB)




Please help, I am at a total loss as to how to fix this. I really do not want to reinstall ubuntu


Thanks

---

### Post by dokaspar on 2009-09-09
Are there any default routes configured? It has happened to me too that default routes are missing after rebooting. Check if you get something like this:

```

$ip route

10.80.17.0/24 dev wlan0  scope link  src 10.80.17.194
default via 10.80.17.1 dev wlan0  [COLOR="DarkRed"]<== is this missing?[/COLOR] 

```

... if there is no default route, then add one like this:

```
sudo ip route add default via wlan0
```

I hope that helps.
Dominik

---

### Post by Rocky1980 on 2009-09-09
When I run *ip route* I get the following output



192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.2  metric 1 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.1.1 dev eth0  proto static

However when I run *ip route* on the live CD i get

192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.2 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.1.1 dev eth0

---

### Post by Rocky1980 on 2009-09-09
Well I have got the net working agian. I used the command 

$sudo ufw disable

So this has turned the firewall off, however it is not a good idea to run without one. Any tips on configing it correctly :confused:

---

