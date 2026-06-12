---
title: "Can't reach any computers on my LAN"
date: 2011-03-12
forum: Networking &amp; Wireless
---

### Post by snufk1n on 2011-03-12
I'm using Ubuntu on my laptop but I'm having a small problem. The network is working fine except for the fact that I can't reach anything on my LAN (can't even ping the router), but everything on the outside works just fine. I can even visit my webserver if I type my public IP.

Where should I begin looking for faults?

Here, enjoy some data. I'm using my wlan0 interface, not sure whether eth0 works or not.
> $ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0


> $ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:1b:fc:94:1d:45  
          inet addr:192.168.0.126  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fe94:1d45/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2531 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3094909 (3.0 MB)  TX bytes:426240 (426.2 KB)


---

### Post by Iowan on 2011-03-12
Two gateways can cause problems. You might try removing the one for eth0 if you don't use it. For that matter - having two interfaces in the same subnet is problematic.

---

### Post by snufk1n on 2011-03-12
Ah, I found a solution. 

I simply added a route:
> route add -net 192.168.0.0 netmask 255.255.255.0 gw 192.168.0.1 dev wlan0
and then everything worked itself out.

---

