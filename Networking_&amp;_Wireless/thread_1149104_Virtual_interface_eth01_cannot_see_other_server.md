---
title: "Virtual interface eth0:1 cannot see other server"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by mikesfx on 2009-05-04
Hi all,

This is a question about virtual ethernet interfaces as configured in /etc/networking/interfaces.

**The Situation**
I'm using the network layout of: cable modem, router, and 192.168.x.x network. My router is 10/100, and to expand the ports on it I connected an external 10/100/1000 switch to one of the extra ports on the router.

Basically what I am trying to do is connect two computers I am using as servers to that switch (which is connected to the router), and have them communicate amongst themselves on their own network of 10.10.10.x, at gigabit speeds (on the switch), but when they need to access the internet they would go through the router like usual. The "server" computers only have 1 physical network card so I have to use virtual IP addresses.

To accomplish this I set up a virtual interface eth0:1 , on each server. Server #1 gets 10.10.10.1/255.255.255.0, server #2 gets 10.10.10.2/255.255.255.0 . 

```

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.1

#virtual interface for communicating at 1gbit
auto eth0:1
iface eth0:1 inet static
address 10.10.10.1
netmask 255.255.255.0
broadcast 10.10.10.255
mtu 9000

```

I have the same setup on the other server except it's eth0 is 192.168.1.4 and eth0:1 is 10.10.10.2

[B]Here's the problem:
[/B]
I can't get the two servers to ping / see eachother on 10.10.10.x -- when I try to ping 10.10.10.1 from 10.10.10.2 it gives me a "destination host unreachable" error.

Here is the route information:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
10.10.10.0      *               255.255.255.0   U     0      0        0 eth0
default         router          0.0.0.0         UG    100    0        0 eth0

```

**Other Notes**

I don't have any routing/switching equipment that supports VLANS, so I was trying to do it with virtual addresses. Can this project *only* be accomplished with VLANS?

Thanks in advance for your help,

-Mike

---

