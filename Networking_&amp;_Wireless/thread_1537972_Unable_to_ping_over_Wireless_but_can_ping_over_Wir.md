---
title: "Unable to ping over Wireless but can ping over Wired."
date: 2010-07-24
forum: Networking &amp; Wireless
---

### Post by pwn on 2010-07-24
I have two machines on this network, one running Ubuntu and the other running Fedora.

When I'm using the Wireless network on the Ubuntu machine, I cannot ping the Fedora machine. Everything else works. I can browse the net fine.

If I switch over to the Wired Network then I can ping the other machine.

I don't understand why ping doesn't work only over the Wireless. I can ping the router so I'm guessing it's getting blocked by the router but I didn't block ICMP traffic.

I tried asking on IRC and they ran out of ideas too to find out where the problem is.

---

### Post by Iowan on 2010-07-24
I doubt this will help, but with wireless active, check **route -n**. I suspect all will be kosher  since you can ping the router, but just in case...

---

### Post by pwn on 2010-07-24
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     2      0        0 eth2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth2
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 eth2

```

Router's IP is 10.0.0.1

---

### Post by Iowan on 2010-07-24
eth2? Is that what your wireless interface is called? (My laptop calls wireless eth1.) If so, then the routing looks kosher...

---

### Post by pwn on 2010-07-24
Yes, eth2 is my wireless card.

So what else can I do to find out where the problem is?

---

### Post by mailias on 2010-07-27
I have the same problem. Anyone any ideas?

(I am a bit confused though that I get the same IP address no matter whether I use wireless or wired lan).

---

### Post by fast_ian on 2010-07-27
> **pwn said:**
> When I'm using the Wireless network on the Ubuntu machine, I cannot ping the Fedora machine..

Can Fedora ping Ubuntu (wirelessly, obviously ;))?

---

### Post by pwn on 2010-07-29
> **fast_ian said:**
> Can Fedora ping Ubuntu (wirelessly, obviously ;))?

Not over wireless. Works if Ubuntu machine is on wired.

I did a traceroute and it seems it's not reaching the router.

---

