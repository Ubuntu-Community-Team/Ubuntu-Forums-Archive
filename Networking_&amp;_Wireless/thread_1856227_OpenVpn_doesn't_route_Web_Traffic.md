---
title: "OpenVpn doesn't route Web Traffic"
date: 2011-10-07
forum: Networking &amp; Wireless
---

### Post by aliov_85 on 2011-10-07
Hello,
I've configured OpenVPN on the server. I can connect to the VPN server but the internet doesn't work. I pretty sure that iptables is not well configured. Probably I didn't configured it well. Below is the commands I entered for iptables:
```
iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE
```
```
iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o tun0 -j MASQUERADE
```
```
iptables -t nat -A POSTROUTING -s 10.8.0.0/32 -o tun0 -j MASQUERADE
```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr aa:00:00:f5:49:d5  
          inet addr:173.245.73.213  Bcast:173.245.73.255  Mask:255.255.255.0
          inet6 addr: fe80::a800:ff:fef5:49d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7931390 errors:0 dropped:0 overruns:0 frame:0
          TX packets:148490 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1311239485 (1.3 GB)  TX bytes:38493630 (38.4 MB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:987 errors:0 dropped:0 overruns:0 frame:0
          TX packets:987 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:79928 (79.9 KB)  TX bytes:79928 (79.9 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.1  P-t-P:10.8.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Thanks for any help

---

### Post by wan.h.yim@gmail.com on 2011-11-01
Same for me.

I have setup a client and server successfully using the simplest how-to here.  I redirect all client traffic to the vpn using the redirect-gateway directive in the config file.

Both client and server are Linux Ubuntu machines. (EC2 server).  How can I use iptables on the client instead of redirect-gateway?

I have spent days searching for examples.  Surprisingly there's very little on that, and nothing works.

It comparison, it's simple to use iptables to redirect all the tcp and DNS traffic to TOR.  The example there works.

I don't know this is needed, 
sudo echo 1 > proc/sys/net/ipv4/ip_forward
because it got fsync errors.  I remembered doing something like that on the server without problems.

The reason for using iptables is that I found out how to, for example, direct some users and not others to the vpn.

---

