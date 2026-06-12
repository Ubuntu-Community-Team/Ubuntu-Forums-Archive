---
title: "CIDR and IPTables"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by sci-fi guy on 2008-12-03
I have started playing around with IPTables, and could use some confirmation that I have a firm grasp on the behavior of CIDR. Currently, I have:
```

ACCEPT     all  --  192.168.0.0/16       anywhere            
ACCEPT     all  --  10.0.0.0/8           anywhere            
DROP       all  --  anywhere             anywhere

```
in it's own chain. Now, if I'm right, the first entry allows packets on 192.168.x.x networks, and the second one allows them on 10.x.x.x networks. Changing the second entry to 10.0.0.0**/16** would limit the range to 10.0.x.x networks, right?

---

### Post by Iowan on 2008-12-05
I'm no expert (nor did I stay at Holiday Inn Express last night), but changing the second entry to 10.0.0.0/16 should *include* the 10.0.x.x range.

---

### Post by jonobr on 2008-12-05
Hello

Open to correcting , but what you are doing here is actually not CIDR,
(Classless Inter domain routing) but classful.

If you look at the IP address and the /number you are using,
its easier to convert to binary.

there are four octets to an IP addres eg 192.168.20.20
each would be represented as a binary number.


PArt of this is a network address and part of it defines a host on your network.


so if you use a /16 this means the first 16 bits are the network address whereas the second 16 is the hosts
in this case the 192.168 is the network portion 
and 20.20 is the host on the 192.168 network

If you were to define a /24 ( 8+8+8 )  then this would be 
192.169.20 is the network address, whereas .20 is the host.

Of course doing this in groups of 8 meant with reali IP address, the amount of hosts and networks was very limited, and was going to run out in the early 90's.
This is when CIDR was introduced, this allowed for variable length subnets, eg, /18  
This would mean part of the 3rd octet (the first two) bits in the 3rd octet would be used as the network address and the last 6 bits of the third octet and then last 8bits of the last octet.

Probably too much info for you, but I enjoyed writing it

---

### Post by sci-fi guy on 2008-12-05
> **Iowan said:**
> I'm no expert (nor did I stay at Holiday Inn Express last night), but changing the second entry to 10.0.0.0/16 should *include* the 10.0.x.x range.

But it would not include the 10.1.x.x range or any value other than 0 in the second octet, right?

---

