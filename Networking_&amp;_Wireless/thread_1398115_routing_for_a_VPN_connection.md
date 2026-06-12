---
title: "routing for a VPN connection"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by steve.a on 2010-02-04
Hi, i installed the free PacketIX vpn client on my ubuntu 9.04.
it created a virtual network adapter, i was able to configure and connect to the VPN service but when i add a default route to the routing table so that all internet traffic goes through the VPN, my internet connection stops working until i remove the line i added.

here's my routing table before :
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.222.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 vpn_vpn
0.0.0.0         192.168.222.2   0.0.0.0         UG    0      0        0 eth0
```

and after i add the route:
```
192.168.222.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 vpn_vpn
10.0.0.0        10.0.0.1        0.0.0.0       U     0      0        0 vpn_vpn
```

here's the virtual network adapter configuration :
```
ifconfig vpn_vpn
vpn_vpn   Link encap:Ethernet  HWaddr 00:ac:55:bc:9e:bf  
          inet addr:10.4.80.192  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::2ac:55ff:febc:9ebf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34625 errors:0 dropped:0 overruns:0 frame:0
          TX packets:298 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:3176333 (3.1 MB)  TX bytes:16090 (16.0 KB)
```

i installed the same VPN client on windows XP and it's working like a charm. please help me to fix it on linux, i don't want to be forced to using windows again.

---

### Post by xcorex on 2010-02-08
Same here. Instead of the last sentence.

---

### Post by afrodeity on 2010-12-12
could you explain how you went about installing the packetx client?

I found this [http://wan.pengganas.net/entry/packetix-net-vpn-installation-on-linux/](http://wan.pengganas.net/entry/packetix-net-vpn-installation-on-linux/)

Surely there is a way to do this with network manager?

---

