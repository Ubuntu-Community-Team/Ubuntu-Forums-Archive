---
title: "Question about duplicate routing table entries"
date: 2005-12-14
forum: Networking &amp; Wireless
---

### Post by cwaldbieser on 2005-12-14
I have a question concerning routing table entries.  The way I understand it, when you want to send a packet, the kernel tries to match the network part of the destination against the network part of each of the entries in the routing table to find out which route to take.

I have seen examples where tables have been set up with duplicate entries-- most often 2 default (0.0.0.0) routes for a computer with 2 NICs.

How does the kernel decide which route to use in this case?  Does one entry always take precedence over the other?  Is the choice made on a case by case basis (and is perhaps arbitrary)?

If there is some sort of precedence in this case, what would it be?

As an experiment, I added started with my normal routing table:
```

$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

```

Next, I added another default route as my loopback device
```

$ sudo route add -net default gw 127.0.0.1
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         localhost.local 0.0.0.0         UG    0      0        0 lo
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

```

At this point, if I tried to ping [www.google.com](www.google.com), I would get a timeout.  I removed the route with
```

$ sudo route del default
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

```

So it looks like the last entry added takes precedence for duplicates-- would this be a correct assessment of the situation?

---

### Post by Lambert on 2005-12-14
Hello cwaldbieser, guess this came from the other thread you were in. 

I learned something through that and this post.

quote from [here]("http://http://www.fandelem.com/nhf-2.html").

> If you get the error: [SIZE=3]Connection timed out[/SIZE] (or similiar.. from a ping, etc) it could be because you have two default gateways set.  Ripped from Microsoft: *This requirement is a result of the basic architecture of TCP/IP. Only one default gateway must be defined on a host that resides on 2 or more non-connected networks.*  Which basically means that for every NETWORK you are on (such as 192.168.0.0) you must have only ONE default gateway. If you have two default gateways, the TCP/IP stack will assume that they lead to the same set of networks; which will cause the server to send Internet traffic to the internal network, *or* internal traffic to the Internet. Overall, you should _not_ have two default gateways. 
interesting notes on failover from [here]("http://www.sustworks.com/site/prod_ipnrx_help/html/RoutesHelp.html")
Not sure about failover with linux though

> 
**Notes on Automatic Failover**

         Some network stacks allow specifying more than one default gateway and use "Dead Gateway Detection" to automatically select the next default gateway if the current gateway fails. The BSD stack used in Mac OS X intentionally separates the routing mechanism (table) from the routing policy (how values in the table are modified). There can be only one default gateway at a time, but it can change based on the routing policy implemented by other software.
         

But I'm curious, you used the loopback interface and got the time out. In the other thread  he set up dual interfaces, each with it's own default gateway, it's not really a dual gateway set up. There's one gateway for each interface. So I wonder what path is being used for his traffic?

---

### Post by cwaldbieser on 2005-12-14
[QUOTE=Lambert]Hello cwaldbieser, guess this came from the other thread you were in. 

I learned something through that and this post.

quote from [here]("http://http://www.fandelem.com/nhf-2.html").

 
interesting notes on failover from [here]("http://www.sustworks.com/site/prod_ipnrx_help/html/RoutesHelp.html")
Not sure about failover with linux though



But I'm curious, you used the loopback interface and got the time out. In the other thread  he set up dual interfaces, each with it's own default gateway, it's not really a dual gateway set up. There's one gateway for each interface. So I wonder what path is being used for his traffic?[/QUOTE]
I am not sure-- I don't have another real NIC, which is why I was experimenting with lo.  My guess would be that only one of his defaults are being used-- performing a traceroute a number of times would probably reveal what's going on.

---

