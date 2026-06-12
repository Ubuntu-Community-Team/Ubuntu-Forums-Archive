---
title: "Static Routing"
date: 2009-06-11
forum: Networking &amp; Wireless
---

### Post by Ubunt2u on 2009-06-11
Ok I've worked half the day on this and for some stupid reason can't get it to work.  Setup is pretty straightforward.  I have 3 NIC's each on a different subnet.  I need to configure static routing for them.

Ip addressing is as follows

eth0 192.168.1.75  gw 192.168.1.1
eth1 192.168.2.75
eth2 192.168.3.75

I've read through multiple how-to's and none of them are the same and none of them have worked.
Would someone PLEASE tell me the proper method for configuring static routes for these subnets?  Thanks in advance.

---

### Post by wirelessmonkey on 2009-06-11
Is 192.168.1.1 your default route, or do you need to set a different route for each interface?

---

### Post by Ubunt2u on 2009-06-11
192.168.1.1 is the default

---

### Post by wirelessmonkey on 2009-06-11
If it's the default, then you shouldn't need to set a static route....
Give me the output of
```
 route 
```

---

### Post by Ubunt2u on 2009-06-11
well, maybe i'm just confused.  i guess i need a static route for each one then.

---

### Post by wirelessmonkey on 2009-06-11
Is each interface going to either; a port on a seperate vlan, or a seperate switch/router? Can you describe exactly what you're trying to do here?

This may be as simple as 
```

sudo -i
echo "0" > /proc/sys/net/ipv4/conf/all/rp_filter

```

But it really depends on how your infrastructure is setup, and what exactly you're trying to do.

---

### Post by Ubunt2u on 2009-06-11
all 3 are going to separate switches

---

### Post by wirelessmonkey on 2009-06-11
Okay....
Then from "man route"
```

route add -net 192.56.76.0 netmask 255.255.255.0 dev eth0
   adds a route to the local network 192.56.76.x via "eth0".  The word     "dev" can be omitted here.

```

Do this with whatever your route should be for each interface, and you should be good to go.

---

### Post by Ubunt2u on 2009-06-11
Ok, so....
route add -net 192.168.1.0 netmask 255.255.255.0 dev eth0

should work?

---

### Post by wirelessmonkey on 2009-06-11
Yes, and 
route add -net 192.168.2.0 netmask 255.255.255.0 dev eth1
route add -net 192.168.3.0 netmask 255.255.255.0 dev eth2


Assuming you have the full subnets.

---

### Post by Ubunt2u on 2009-06-11
man oh man i feel dumb, i forgot to enable ip forwarding.  all is good now thanks for the help

---

