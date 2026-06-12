---
title: "lan to differnet subnets and tracert command"
date: 2013-01-06
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2013-01-06
I have a win7 to router to router to ubuntu pc (10.42.0.1)to win7 (10.42.0.19) configuration.

What I want is to be able to ping win7 to win7
I ran tracert on the first win7
tracert 10.42.0.1 connects all the way to ubuntu PC.
tracert 10.42.0.19 wont get there to other win7 PC.

So do I need a route add  to the ubuntu NIC to route packets to 
10.42.0.19 ?

current route table is
> ```
scott@scott-P5QC:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         wr850g.hr.cox.n 0.0.0.0         UG    0      0        0 eth2
10.42.0.0       *               255.255.255.0   U     1      0        0 eth0
10.42.0.0       scott-P5QC.loca 255.255.0.0     UG    1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth2
scott@scott-P5QC:~$ 
```


why does this line

10.42.0.0       scott-P5QC.loca 255.255.0.0     UG    1      0        0 eth0

not forward packets going to 10.42.0.xxx locations dynamically automatically?

Does there need to be a line saying
10.42.0.19       scott-P5QC.loca 255.255.0.0     UG    1      0        0 eth0


Pictures showing win7 tracert command results

---

### Post by sdowney717 on 2013-01-06
It is slightly more complex lan than this.

I have 2 nics in the ubuntu PC and I share the internet to the last win7 pc

So the incoming packets are from 192.168.200.30 (eth2)
and they need to go to 10.42.0.19

10.42.0.xxx is the gigabyte lan. (eth0)

I tried adding a route but still not reachable.

```
scott@scott-P5QC:~$ sudo route add -net 10.42.0.19 netmask 255.255.255.255 gw 10.42.0.1 metric 1
scott@scott-P5QC:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         wr850g.hr.cox.n 0.0.0.0         UG    0      0        0 eth2
10.42.0.0       *               255.255.255.0   U     1      0        0 eth0
10.42.0.0       scott-P5QC.loca 255.255.0.0     UG    1      0        0 eth0
10.42.0.19      scott-P5QC.loca 255.255.255.255 UGH   1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth2

```

---

### Post by sdowney717 on 2013-01-06
I figure the problem is the ubuntu route table.
Packets go ok from 192.168.200.36 to 10.42.0.1
but next hop is stopped going from 10.42.0.1 to 10.42.0.19

Ubuntu PC itself can ping to 10.42.0.1

---

### Post by sdowney717 on 2013-01-08
Solved by installing webmin!!

I did get a certificate warning, log in anyway!

after you log in to webmin then on left side click
Networking then Linux firewall.

I got a message saying 2 rules had been entered that webmin could not deal with, so saved current iptables to a file.

The I reset the firewall.
And it worked, I can browse shared folders on all the computers. On first win7 pc, I have to map network drive since it is in a different subnet.

The webmin shows a very nice gui to the firewall configuration!


[IMG]https://lh4.googleusercontent.com/-JLN674cmEuc/UOx_lsKNoNI/AAAAAAAAEXo/GtGZ8LHzexA/s1440/fixedfirewall.png[/IMG]

---

