---
title: "Ping An IP range outside my IP range"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by CrusaderAD on 2009-09-29
Ok, here's my setup. I have a router giving all of my local machines an IP through DHCP. Plugged into the router I have my wireless router pulling a static IP address. The Wireless then pulls the internet connection and such while distributing it's own IP range. How can I ping a machine connected to the wireless from a machine plugged into the original router? Example:

Wireless machine IP on wireless router: 192.168.1.100
Wired Machine IP on wired router: 192.168.2.100

Pinging 192.168.1.100 from 192.168.2.100 doesn't work. Any ideas?

---

### Post by fishy6969 on 2009-09-29
I might be missing something here, but why not assign your wireless router a static IP of 192.168.**1**.101 and turn off it's DHCP server. Wireless clients would then get an IP from the wired router. Or is there a reason why you want to run wired on 192.168.1.* and wireless on 192.168.2.* ?

---

### Post by Brandon Williams on 2009-09-29
I assume that you've used a full 24 bit (class C) subnet mask for the two subnets, such that the two subnets are viewed as different networks for routing purposes. If this is true, then each of your routers would need to be told (via a routing table entry) how to get to the other subnet.

Alternatively, each of the routers could be multi-homed (one IP address on each subnet) or you could shorten the subnet mask down to 22 bits (255.255.252.0) so that both 192.168.1.N and 192.168.2.N are on the same subnet, which means that the routers. This will only work if what you really have is a pair of internet gateways (routers with builtin switches) and the two switches are daisy-chained together.

---

### Post by CrusaderAD on 2009-09-30
> **fishy6969 said:**
> I might be missing something here, but why not assign your wireless router a static IP of 192.168.**1**.101 and turn off it's DHCP server. Wireless clients would then get an IP from the wired router. Or is there a reason why you want to run wired on 192.168.1.* and wireless on 192.168.2.* ?

This worked. I should have figured this out. Thanks for the replies!

---

