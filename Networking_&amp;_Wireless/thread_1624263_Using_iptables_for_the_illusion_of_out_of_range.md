---
title: "Using iptables for the illusion of out of range"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by htpw16 on 2010-11-17
Hello all,

I have a question about using iptables. I have a number of wireless devices that I use for research. I am limited by physical space so I can only place them where they can all see each other. However, I want to create the illusion of a wireless device being out of range of another using iptables (resulting in basically a two path topology): 
```

  [COLOR="Blue"]4--5--6[/COLOR]
 /       \
1         7 
 \       /
  [COLOR="Sienna"]2-----3[/COLOR]

```
I have tried dropping all packets that are not a direct neighbor to a device. But this obviously does not allow for a device to be discoverable since a ping would be dropped due to the source not being a direct neighbor etc. I have also tried allowing pings (-p icmp) on each device, however, even though it would correctly follow a particular path in the routing table, if a device failed, say device 6, on that path, the ping still reaches its destination since icmp is allowed. Where, in practice, if the link 6-7 does not exist, 7 should not be reachable on that path. 

This leads me to believe that ping does not use routing tables for its routes. I dunno...

Any suggestions from you experts are greatly appreciated.

Thanks,

-htpw16
iptables newbie

---

