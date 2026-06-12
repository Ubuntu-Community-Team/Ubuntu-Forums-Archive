---
title: "Unstable VPN Connection"
date: 2009-10-20
forum: Networking &amp; Wireless
---

### Post by lex1015 on 2009-10-20
G'day, everyone!

I'm new to *nix and I have encountered an issue concerning my VPN connection. If that matters, I use ethernet adapter. The connection lasts for about 5 - 20 minutes (it really ranges from time to time) and then it disconnects - and now these disconnections occur much more often than they used to. When I try to establish VPN again

```
sudo pon vpn
sudo route add default dev ppp0
```I keep getting the following error:

```
SIOCADDRT: Network is down
```Beside Internet, I cannot connect to my LAN's servers as well after it happens.
Chances are, after rebooting or in 20-30 minutes it may eventually connect (and it may not), so I suspect there is some process to kill. Everything's all right in Windows so my LAN doesn't seem to have anything to do with it. 

Here's the ifconfig output after the connection break:

```
eth0      Link encap:Ethernet  HWaddr 00:0e:2e:78:13:a2  
          inet addr:10.49.69.133  Bcast:10.49.79.255  Mask:255.255.240.0
          inet6 addr: fe80::20e:2eff:fe78:13a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33779 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6358 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7053547 (7.0 MB)  TX bytes:1402701 (1.4 MB)
          Interrupt:17 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

```After awhile it may even turn into 

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1088 (1.0 KB)  TX bytes:1088 (1.0 KB)
```So there's another error to deal with:
```

SIOCADDRT: No such device
```I'm clueless. What goes wrong?..

Thanks in advance!

---

