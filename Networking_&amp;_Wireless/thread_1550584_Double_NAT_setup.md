---
title: "Double NAT setup"
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by mbzn on 2010-08-11
Hi,

I have a setup at home and it looks sort of like this:
DSL line to router1(wan side)
Servers to Router1(lan side)
Router2(wan) to Router1(lan)
windoze pc to router2(lan) 
Ubuntu PC to Router2(lan)

All IP's are static and correct... The windoze pc works???
ip for router1-wan 123.123.123.123
ip for router1-lan 192.168.10.1
ip for router1-wan 192.168.10.20
ip for router1-lan 192.168.5.1
My win pc is set-up as 192.168.5.2 mask 255.255.255.0 
and gateway1 192.168.5.1, gateway2 192.168.10.1- and works

So i need to setup this same route for my Ubuntu pc ip-192.168.5.3

I've tried the routes button in Edit connection(right click network icon).
It seems to find a internet connection but times out on any page.
I can ping: my ip, my router2(lan&wan), My router1(lan&wan). so i believe i just don't follow the correct route.

Any help or reading material appreciated.
Thanks alot.

---

### Post by mprokolo on 2010-08-11
I don't really get your setup
but open a terminal and execute 
```
ifconfig
``` 
to see if you have the correct settings 
also for the gateway you can use the
```
route
``` 
command

---

### Post by mbzn on 2010-08-11
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:b9:0b:61:42  
          inet addr:192.168.5.10  Bcast:192.168.5.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe0b:6142/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11578 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8880555 (8.8 MB)  TX bytes:1269289 (1.2 MB)
          Interrupt:16 


route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.5.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.5.1     0.0.0.0         UG    0      0        0 eth0

I believe the route is not setup correctly

I need to connect as follows:
my pc 192.168.5.10
my router2 192.168.5.1 (lan side)
my router2 192.168.10.20 (wan side)
my router1 192.168.10.1 (lan side)
my router1 123.123.123.123(internet address) (wan side)

Thanks for the reply

---

### Post by mbzn on 2010-08-11
Don't worry, i think after i entered the route command the problem is solved. That's what i needed to do.

Than you very much!

---

