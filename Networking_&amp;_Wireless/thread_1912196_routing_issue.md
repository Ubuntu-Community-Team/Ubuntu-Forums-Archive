---
title: "routing issue"
date: 2012-01-20
forum: Networking &amp; Wireless
---

### Post by hssuhle on 2012-01-20
Hello *,
 
this is not a special ubuntu problem - more a linux related problem. 
 
On one of my clients, the routing table looks like this:
 
```
Destination      Gateway            Genmask         Flags Metric Ref    Use Iface
192.168.43.1     *                  255.255.255.255 UH    0      0        0 eth0
192.168.5.0      10.0.150.5         255.255.255.0   UG    0      0        0 tap0
192.168.150.0    10.0.150.1         255.255.255.0   UG    0      0        0 tap0
10.0.150.0       10.0.150.1         255.255.255.0   UG    0      0        0 tap0
10.0.150.0       *                  2555.255.255.0  U     0      0        0 tap0
192.168.43.0     *                  255.255.255.0   U     311    0        0 eth0
default          192.168.43.1       0.0.0.0         UG    0      0        0 eth0
default          192.168.43.1       0.0.0.0         UG    311    0        0 eth0

```Now, whenever I try to traceroute 10.0.150.1, the packet is not being sent towards the tap0 interface, but towards 192.168.43.1 - which however cannot work. 
 
Any suggestion? 
 
Thanks a lot!
 
hssuhle

---

### Post by Charlietje on 2012-01-20
Hi,

How did you made this routing table?
It does not make much sense...

You have 2 default gateways:
```
default          192.168.42.1       0.0.0.0         UG    0      0        0 eth0
default          192.168.43.1       0.0.0.0         UG    311    0        0 eth0
```

You can only have 1 gateway.
You also say that the default gateway is yourself:
```
192.168.43.1     *                  255.255.255.255 UH    0      0        0 eth0
default          192.168.43.1       0.0.0.0         UG    311    0        0 eth0
```


regards

---

### Post by hssuhle on 2012-01-20
Umm. 
You are right saying ther can only be one default gateway. 
However, there IS only one default gateway. One with metric 0 and the same with metric 311. 
Where it comes from - I don't know.

But I agree, I should try without these useless entries.

All I have left now is
```

Destination      Gateway            Genmask         Flags Metric Ref    Use Iface 
192.168.5.0      10.0.150.5         255.255.255.0   UG    0      0        0 tap0 
192.168.150.0    10.0.150.1         255.255.255.0   UG    0      0        0 tap0 
10.0.150.0       10.0.150.1         255.255.255.0   UG    0      0        0 tap0 
default          192.168.43.1       0.0.0.0         UG    0      0        0 eth0

```And still, the packets are going towards 192.168.43.1 - SH*T!

More ideas?

---

### Post by Charlietje on 2012-01-20
> However, there IS only one default gateway. One with metric 0 and the same with metric 311. 
Where it comes from - I don't know.

No, they are not the same. The fist is 192.168.42.1 and the second is 192.168.43.1 



What is the output of: ```
ifconfig
```

---

### Post by SeijiSensei on 2012-01-20
You're missing the route to the 192.168.42.0/24 network.  The machine can't see the default gateway with the configuration you have now.

---

### Post by hssuhle on 2012-01-20
Uh - NOW I see what you mean! 

My apologies!

As I had to type the routing table off by hand (since I cannot log into the device whilst it is on vpn), I must have mis-typed that. 

As a matter of fact, it reads 43. NOT 42. Apologies, again!

Nevertheless, it makes the whole thing appear even stranger, doesn't it?

ifconfig tap0 reads:
```
tap0: ip 10.0.150.9 mask 255.255.255.0 flags [up broadcast running multicast]
```

ifconfig eth0:
```
eth0: ip 192.168.43.92 mask 255.255.255.0 flags [up broadcast running multicast]
```

---

