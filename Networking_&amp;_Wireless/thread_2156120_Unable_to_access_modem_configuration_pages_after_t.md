---
title: "Unable to access modem configuration pages after they are set to bridge mode"
date: 2013-06-20
forum: Networking &amp; Wireless
---

### Post by Vpc on 2013-06-20
When I run my SpeedTouch ST516 and TP-Link TD8616 modems in bridge mode I am unable to access their configuration pages. I am able to connect to the internet through the modems with with a PPPoE connection from Network Manager (created by going to Edit Connections -> DSL -> Add).

In my file /etc/network/interfaces
```
# The loopback network interface
auto lo
iface lo inet loopback
```

The default ip for the SpeedTouch ST516 is [http://192.168.1.254](http://192.168.1.254) but when it's being used in bridge mode the default gateway is shown as [http://206.248.154.104](http://206.248.154.104)

Output of 'route':
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         206.248.154.104 0.0.0.0         UG    0      0        0 ppp0
link-local      *               255.255.0.0     U     1000   0        0 ppp0
206.248.154.104 *               255.255.255.255 UH    0      0        0 ppp0

```
Output of 'ifconfig':
```
eth1      Link encap:Ethernet  HWaddr 38:60:77:d5:9b:27  
          inet6 addr: fe80::3a60:77ff:fed5:9b27/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31946 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21690 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41466008 (41.4 MB)  TX bytes:2591890 (2.5 MB)
          Interrupt:20 Memory:fe700000-fe720000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:836 errors:0 dropped:0 overruns:0 frame:0
          TX packets:836 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:80909 (80.9 KB)  TX bytes:80909 (80.9 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:69.165.145.225  P-t-P:206.248.154.104  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2916 (2.9 KB)  TX bytes:2523 (2.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:e9:f6:e5:c6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I can no longer access [http://192.168.1.254/](http://192.168.1.254/) and when I try [http://206.248.154.104](http://206.248.154.104) in my browser I get
"Not Found
Url not found: /"

The default ip for the TP-Link TD8616 is [http://192.168.1.1](http://192.168.1.1) but when the modem is in use, the default gateway is shown as [http://206.248.154.104](http://206.248.154.104)

Output of 'route'
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         206.248.154.104 0.0.0.0         UG    0      0        0 ppp0
link-local      *               255.255.0.0     U     1000   0        0 ppp0
206.248.154.104 *               255.255.255.255 UH    0      0        0 ppp0

```

Output of 'ifconfig'
```
eth1      Link encap:Ethernet  HWaddr 38:60:77:d5:9b:27  
          inet6 addr: fe80::3a60:77ff:fed5:9b27/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1911 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1899 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2081051 (2.0 MB)  TX bytes:362377 (362.3 KB)
          Interrupt:20 Memory:fe700000-fe720000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:627 errors:0 dropped:0 overruns:0 frame:0
          TX packets:627 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53584 (53.5 KB)  TX bytes:53584 (53.5 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:69.165.155.102  P-t-P:206.248.154.104  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:1903 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1799 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2030991 (2.0 MB)  TX bytes:295268 (295.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:e9:f6:e5:c6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

I cannot access [http://192.168.1.1/](http://192.168.1.1/) and when I try [http://206.248.154.104](http://206.248.154.104) in my browser I get
"Not Found
Url not found: /"

---

