---
title: "Nic bonding, mode 1 on two mode 0's"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by ubumand1000 on 2010-02-09
Hi,

I have a server which has four ports. There are two switches, one which has access to the internet and is 100 Mb switch. The other is a 1 Gb switch. The two switches are interconnected.

What I want to do is load balancing with two ports on the 1 Gb switch. If the 1 Gb switch fails, I want that the server fails over to the other two ports which are connected to the 100 Mb switch. So what I want to do is a mode 1 bonding on two mode 0 (with each 2 ports) configurations.

Is this possible?

If it is possible, what if only one port on the 1 Gb switch gets down? Will the server failover to the low speed switch or will it wait until the second port also fails?

A presentation of what I want to do:

[IMG]http://i50.tinypic.com/69fkgh.jpg[/IMG]


Thanks.

---

