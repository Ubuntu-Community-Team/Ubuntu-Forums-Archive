---
title: "Daisy chaining routers question"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by kerryhall on 2009-10-07
If I have two routers daisy chained, and the parent is 192.168.0.1, and the child is 192.168.1.1, is it possible for computers on 192.168.0.* to access computers on 192.168.1.* ? I have had success going from x.x.1.* to x.x.0.* but not vice verse.

---

### Post by Brandon Williams on 2009-10-07
If these are internet gateway home routers, then you're really daisy chaining two switches, not two routers. With this configuration, it's recommended to configure them both on the same subnet. Otherwise, you'll have to configure the inidividual computers so that they know that both subnets are on the same LAN.

---

### Post by kevdog on 2009-10-07
I suppose you could do this if the router somehow could route the packets with some form of translation such as used with a VPN.

---

### Post by RealG187 on 2009-10-07
I think you would have to configure the child's default gateway to the first one.

---

### Post by the_dark_light on 2009-10-08
If it's anything like the Linksys WRT type then you should be able to change one of them from gateway mode to router mode.  This may allow communication between both segments.

---

### Post by p1t0u on 2009-10-08
As long as you are using the router in NAT mode port forwarding would be the only way to come in to the child network.  Depending on the kind of access you would like that may or may not be acceptable.  Otherwise if your router allows it, going to bridge mode would make everyone part of the same network and give you full access.

---

