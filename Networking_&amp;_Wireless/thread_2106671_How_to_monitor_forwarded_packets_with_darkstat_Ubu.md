---
title: "How to monitor forwarded packets with darkstat Ubuntu 12.04"
date: 2013-01-19
forum: Networking &amp; Wireless
---

### Post by psyllex on 2013-01-19
[SIZE="2"]**I have a little network I'm trying to monitor.  I've used darkstat to monitor all machines.  ON my servers it works perfectly as well as my desktop.  On my routers I have a VLAN that contains a subnet.  How can I track the packages that are forwarded through the router but not addressed to the router itself?  Or is this point not really necessary because my end server that the packets are addressed to will monitor those packets? ** 

t**he manpage says to use -l 192.168.1.0/255.255.255.0 to monitor all traffic through a network given the localhost is part of that network.  But when I do this I get sketchy results in my graphs:**
 [IMG]http://johnverber.com/with.png[/IMG].  

**If I'm monitoring a machine I get a steady flow of in/out traffic with no gaps** [IMG]http://johnverber.com/without.png[/IMG].  


[B]But when I try and monitor all traffic through the network with the -l command it starts to skip anything comming in and it seems to miss intervals.  

Can anyone help me out with this?  Thanks alot![/B][/SIZE]

---

### Post by ljube on 2014-01-11
first, tell me at which instance do you use darkstat? Which server has the darkstat on? Or all machines have darkstat?

---

