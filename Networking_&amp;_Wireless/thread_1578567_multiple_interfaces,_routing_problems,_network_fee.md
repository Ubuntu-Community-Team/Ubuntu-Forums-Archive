---
title: "multiple interfaces, routing problems, network feeb..."
date: 2010-09-20
forum: Networking &amp; Wireless
---

### Post by travisnoll on 2010-09-20
I'm running Ubuntu 10.04.1 as a guest OS under Virtualbox on a Win7 host.  Most of the work I do runs fine from the laptop, weather it is wired on my desk or using wireless in meetings and such.  The problems arose after I installed apache and sshd.  I believe traffic initiated by other machines is being routed back over eth0 and is ignored because it's not coming from the expected address.

```

me@myhost:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:27:f8:e5:6a  
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fef8:e56a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21773 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54795734 (54.7 MB)  TX bytes:4009676 (4.0 MB)

eth1      Link encap:Ethernet  HWaddr 08:00:27:01:13:78  
          inet addr:AAA.BBB.102.68  Bcast:AAA.BBB.102.127  Mask:255.255.255.128
          inet6 addr: aaaa::bbbb:cccc:dddd:1378/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:361699 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34341974 (34.3 MB)  TX bytes:253949 (253.9 KB)

```eth0 is my first virtual adapter, running under NAT so I can use the connectivity of my host.  eth1 is bridged to the Intel adapter so it only works when my machine is wired on my desk, and I'm fine with that.

```

me@myhost:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
AAA.BBB.102.0   *               255.255.255.128 U     1      0        0 eth1
10.0.2.0        *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         10.0.2.2        0.0.0.0         UG    0      0        0 eth0

```Please note I've tried to anonymize my IP so as not to paint a network feeb target on my back.

If I turn off eth0, sshd and apache work fine from another machine, but I have to keep turning things on and off when I move my machine around.  I believe I need help configuring routing and some rules so the thing behaves as I expect -- traffic initiated by remote hosts sends responses out over eth1, but "my" traffic uses eth0 to take advantage of the windows integration with the 802.11 network I'm committed to by my employer.

Much thanks! -- travis

---

### Post by travisnoll on 2010-09-28
I've tapped a bunch of co-workers on this one, and read quite a bit of documentation to get this working.  I would like to clean things up and automate the routing on startup but this is what I've done:

lines added to /etc/iproute2/rt_tables
```
# create a route table for the nat interface
77    nat
# create a route table for the wired interface
88    wired
```I found I have 256 routing tables to work with, numbered 0-255.  77 and 88 are arbitrary indexes and I've named them for their application.

the route configuration I run looks like this:

```
        #build routes to our gateways
        ip route add 10.0.2.0/24 dev eth0 src 10.0.2.15 table nat
        ip route add AAA.BBB.102.0/25 dev eth1 src AAA.BBB.102.68 table wired

        #default routes via those gateways      
        ip route add default via 10.0.2.2 table nat
        ip route add default via AAA.BBB.102.126 table wired

        #main routing table -- what happens if our nat address changes?   
        ip route add 10.0.2.0/24 dev eth0 src 10.0.2.15
        ip route add AAA.BBB.102.0/25 dev eth1 src AAA.BBB.102.68

        #our preferred default route      
        ip route add default via 10.0.2.2

        #routing rules define what table to use.          
        ip rule add from 10.0.2.15 table nat
        ip rule add from AAA.BBB.102.68 table wired

        #Flush the cache to make effective
        ip route flush cache
```...but I've run it by hand and I would like to know if there is a conventional place in Ubuntu to do this sort of thing on startup.  And some feedback as to how my narrow grasp on the subject matter has led me to overlook a more elegant solution!

-Travis

---

