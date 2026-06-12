---
title: "Properly IP Alias"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by UltraDangerLord on 2010-03-16
Hello All,

I'm trying to add an IP alias to my ethernet device. It doesn't seem to be working permanently. 

I've tried these few things below. This works for the moment, but once the server is restarted, the IP is lost

```

sudo /sbin/ifconfig eth0:1 192.168.50.36 up

```

This works for the moment, but once the server is restarted, the IP is lost

I've edited /etc/network/interfaces and put this code in, which doesn't seem to be working

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address         192.168.50.1
        netmask         255.255.0.0
        gateway         192.168.123.1
        broadcast       192.168.1.255

iface eth0:1 inet static
        address         192.168.50.36
        netmask         255.255.0.0
        gateway         192.168.123.1
        broadcast       192.168.1.255


```

There must be something I'm forgeting, all the google results on this topic are dated and confusing for me to read. 

Any suggestion will be greatly appreciated

---

### Post by UltraDangerLord on 2010-03-16
Bump!?

---

### Post by Iowan on 2010-03-17
I've heard of aliasing IP's in different subnets - but dunno if two in the same subnet will work (although you say it works manually). 
I doubt it's the problem, but "standard" broadcast address for that subnet would be 192.168.255.255.

---

