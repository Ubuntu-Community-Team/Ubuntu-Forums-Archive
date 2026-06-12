---
title: "Two NICs, one big headache."
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by antareus on 2009-02-21
Disclaimer: I'm a total hack when it comes to networking and routing. But I've lost enough hair to this, and this is a weird situation, so take some pity on me.

I'm running on Ubuntu 8.04 using two NICs to communicate with two separate networks. Except, the configuration is a bit different from what you'd normally see:
```

# ifconfig eth0 192.168.1.30
# ifconfig eth1 192.168.1.30

```
Yep, same IP and subnet, but two different networks that happen to be set up identically, but cannot be connected together (for testing). I need to be able to communicate with computers on each subnet using a management application, developed by me. Ideally, I'd want to be able to jail a process into only using one network interface to communicate with, no matter what. But the problem manifests itself in a simpler situation.

When I try to run a simple ping, I hit a wall.
```

# ping -I eth0 192.168.1.1
# ping -I eth1 192.168.1.1

```
Ping, in both cases, mentions that it is bound to the interface, and the IP of the interface before it starts sending out pings. But only eth0 receives replies. Running tcpdump on eth1 shows that replies are coming in, but they don't make it back to ping for some reason. I think the order of entries in the routing table is causing this, I can delete eth0's entry, and then eth1 starts working.

Now, if I use different IPs on each interface, then I can set up policies to route it correctly. But I don't have that luxury, unfortunately. There has to be a way to do this, since you can do a ton of cool stuff with the iproute2 package.

---

### Post by superprash2003 on 2009-02-21
i dont think its recommended to use the same ip for both interfaces...

---

### Post by mpokrywka on 2009-02-21
It is default kernel setting to ensure networking works deterministic, your configuration is little unusual, but you seem to know better and can override "safety locks" ;)
Use:
echo 0 > /proc/sys/net/ipv4/conf/eth1/rp_filter

This turns off reverse route path filtering that ensures that packets that are received by kernel comes from corect devices according to routing rules.

---

### Post by antareus on 2009-02-21
Good heavens, you just saved me a LOT of time coding and testing code.

Thank you and check your PMs.

---

