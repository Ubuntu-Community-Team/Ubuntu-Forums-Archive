---
title: "Networking a Strange Way"
date: 2011-11-21
forum: Networking &amp; Wireless
---

### Post by Arukas on 2011-11-21
Hello-

I have two devices I am trying to make talk to each other, but they are on different subnets.  The simple solution would be to put them on the same subnet but that will be no fun.

My question is how do I go about it?  I'm not for sure where to start.  Most places, I read dodge the issue by saying "not" to do it.  I want to do it.

Where do I need to look?  Do I need routers for each device?

-Thanks

---

### Post by An Sanct on 2011-11-21
if you have multiple routers, expand your Class C network.

Please read this docs [IPv4 subnet ref.]("http://en.wikipedia.org/wiki/IPv4_subnetting_reference") and [Subnetwork]("http://en.wikipedia.org/wiki/Subnetwork").

To my understanding, you would have to set the netmask of all routers to *255.255.0.0*, to expand the local "Class C" network to multiple subnetworks (192.168.0.1 -> 192.168.255.254)

This is just a guess according to my network knowledge, nothing personally tested...

---

### Post by jonobr on 2011-11-21
> To my understanding, you would have to set the netmask of all routers to 255.255.0.0, to expand the local "Class C" network to multiple sub networks (192.168.0.1 -> 192.168.255.254)

Correction here, Class C addresses uses a 255.255.255.0 or /24 netmask.

Class B would be 255.255.0.0 or /16 subnet mask.

To connect together two devices from two different subnets you need a router.
It could be a commercial router (not the residential ones that connect your LAN to a DSL or cable port) or it could be an Ubuntu machine with a second NIC which is set up to route between the subnets,



There are other ways, but the cheapest and simplest method is probably changing IP and using a switch if you have that ability.

---

### Post by bab1 on 2011-11-21
> **Arukas said:**
> Hello-

I have two devices I am trying to make talk to each other, but they are on different subnets.  The simple solution would be to put them on the same subnet but that will be no fun.

My question is how do I go about it?  I'm not for sure where to start.  Most places, I read dodge the issue by saying "not" to do it.  I want to do it.

Where do I need to look?  Do I need routers for each device?

-Thanks

If you have 2 networks (subnets) then you need to connect them to a router (layer 3 device).  This is the essence of Inter-networking.  Devices on the same network (subnet) communicate via layer 2 protocols.  A switch or hub will provide connectivity for layer 2.

Most routers for home and small business combine a router with a switch.  It is not one or the other it is: Inter-networking needs both a switch and a router and local networking (a single network (subnet)) just needs a switch.

---

### Post by bab1 on 2011-11-21
> **jonobr said:**
> Correction here, Class C addresses uses a 255.255.255.0 or /24 netmask.

Class B would be 255.255.0.0 or /16 subnet mask.

...

Another way of looking at this would be to say: if all the hosts have the same subnet mask then they are in the same network (subnet).  There is no "Class" distinction anymore see [**_CIDR_**]("http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing").

---

### Post by An Sanct on 2011-11-21
> **bab1 said:**
> Another way of looking at this would be to say: if all the hosts have the same subnet mask then they are in the same network (subnet).  There is no "Class" distinction anymore see [**_CIDR_**]("http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing").
I also heard of the "Class" distinction only a month ago, in a quiz :)

Maybe I should say "local small/medium network" instead :)

---

### Post by bab1 on 2011-11-21
> **An Sanct said:**
> I also heard of the "Class" distinction only a month ago, in a quiz :)

Maybe I should say "local small/medium network" instead :)

Class distinction is the original method of separating networks.  This allowed for obvious boundaries of IP ranges.  For example the network of 192.168.0.0 /24 (a class C network) has the boundaries of 192.198.0.0 to 192.168.0.255 but what it really looks like is this ```
11000000101010000000000000000000 (192.168.0.0)
to 
11000000101010000000000011111111 (192.168.0.255
```

Neither of those tell you what the network is and what the host is, but if you do this  ```

110000001010100000000000[COLOR="Red"]00000000[/COLOR] (192.168.0.0) # Network ID
111111111111111111111111[COLOR="Red"]00000000[/COLOR] (255.255.255.0) # The network ends where the 1's stop
to 
110000001010100000000000[COLOR="Red"]11111111 [/COLOR](192.168.0.255 # broadcast address
111111111111111111111111[COLOR="Red"]00000000[/COLOR] (255.255.255.0) # The network ends where the 1's stop

```

It is now obvious where the boundaries of the network are.

This network has 24 bits of network mask and 8 bits of hosts.  What happens if you make the network 23 bits of network and 9 bits of hosts?  It looks like this (spaces added for clarity)
 ```

11000000 10101000 00000000 [COLOR="Red"]00000000[/COLOR] (192.168.0.0) # Network ID
11111111 11111111 1111111[COLOR="Red"]0 00000000[/COLOR] (255.255.248.0) # The network ends where the 1's stop

to 
11000000 10101000 00000001[COLOR="Red"] 11111111 [/COLOR](192.168.1.255 # broadcast address
11111111 11111111 1111111[COLOR="Red"]0 00000000[/COLOR] (255.255.248.0) # The network ends where the 1's stop


```

The first network has 254 usable hosts and the second one has 510 usable hosts.  The first number is always reserved for the network ID and the last is the broadcast address for the network.  Just for completeness here is a 192.168.0.0/16 network (65536 hosts)
 ```

11000000 10101000 [COLOR="Red"]00000000 00000000[/COLOR] (192.168.0.0)
11111111 11111111 [COLOR="Red"]00000000 00000000[/COLOR] (255.255.0.0)
to 
11000000 10101000 [COLOR="Red"]11111111 11111111 [/COLOR](192.168.255.255)
11111111 11111111 [COLOR="Red"]00000000 00000000[/COLOR] (255.255.0.0)

```

Edit:  you can also make the network smaller.  What does a 192.168.0.0/25 network look Like I wonder?  Like this
```

11000000 10101000 00000000 00000000 (192.168.0.0)
11111111 11111111 11111111 1[COLOR="Red"]0000000[/COLOR] (255.255.255.128)
to 
11000000 10101000 00000000 01111111 (192.168.0.127)
11111111 11111111 11111111 1[COLOR="Red"]0000000[/COLOR] (255.255.255.128)
```

---

