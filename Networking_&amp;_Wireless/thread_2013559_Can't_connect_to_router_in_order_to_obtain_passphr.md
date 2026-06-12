---
title: "Can't connect to router in order to obtain passphrase"
date: 2012-07-01
forum: Networking &amp; Wireless
---

### Post by chmacka on 2012-07-01
I've just installed Ubuntu 12.04 and I can't connect to the router, even though the system recognizes the wireless network. When I installed Windows I first selected the wireless network and then opened the router settings via 192.168.1.1. There I found the passphrase and was able to establish an internet connection.

But I can't do it in Ubuntu. I select the network (I don't have the passphrase), try to access the router in Firefox with 192.168.1.1 but it just says 'Unable to connect' (unlike in Windows where I would be asked for username and password).

Here's ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:11:2f:c3:b8:22  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:416 errors:0 dropped:0 overruns:0 frame:0
          TX packets:416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:32976 (32.9 KB)  TX bytes:32976 (32.9 KB)

wlan0     Link encap:Ethernet  HWaddr c8:3a:35:cf:26:09  
          inet6 addr: fe80::ca3a:35ff:fecf:2609/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:57 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6441 (6.4 KB)  TX bytes:8721 (8.7 KB)


```

---

### Post by steeldriver on 2012-07-01
Hi, I think you're confusing 2 things:

1. the wireless security (WEP / WPA) credentials (SSID and passkey/passphrase)

2. the router's administration login / password - this is what the  browser prompts you for when you connect via the 192.168.1.1 IP

AFAIK neither Windows nor Linux will let you connect to the router  (stage 2) _wirelessly_ BEFORE supplying the WEP/WPA credentials (stage 1) - if you need to get into the router setup pages via a browser to retrieve these you will have to do that via a temporary _wired_ connection

---

### Post by chmacka on 2012-07-01
Then I guess when I was installing Windows my PC was already wired to to Router and that's how I accessed it. Thanks!

---

