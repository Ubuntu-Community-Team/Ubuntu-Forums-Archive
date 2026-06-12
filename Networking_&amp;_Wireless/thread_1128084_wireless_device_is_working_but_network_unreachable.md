---
title: "wireless device is working but network unreachable"
date: 2009-04-17
forum: Networking &amp; Wireless
---

### Post by jeanluca on 2009-04-17
Hi All

I cannot connect to the internet via wireless device(I used to do it wired)

Anyway, I can connect with my wireless router (I get an IP) but when I try 
```

$> ping www.google.com
ping: unknown host www.google.com

```

When I try to ping the router (my IP is 192.168.1.14) I get
```
$> ping 192.168.1.1
From 192.168.1.14 icmp_seq=1 Destination Host Unreachable
From 192.....
.....

```

Here is the output from 'route'
```

$> route
Kernel IP routing table
Destination     Gateway      Genmask   Flags Metric   Ref    Use  IFace
192.168.1.0     *            255.255.255.0 U   2      0      0   ath0
link-local      *            255.255.0.0   U   1000   0      0   ath0
default         192.168.1.1  0.0.0.0       UG  0      0      0   ath0

```
I don't know what else I can do to find the problem, any suggestions ?

Thnx a lot
LuCa

ps I use the same router for my laptop and that works fine!

---

### Post by jeanluca on 2009-04-17
it turned out that my firewall shorewall only allowed eth0 to do internet stuff. Turning it off fixed the ping/access problem to my router, but not to google (I also tried to restart networking). But after a reboot everything worked just fine :)

cheers
LuCa

---

