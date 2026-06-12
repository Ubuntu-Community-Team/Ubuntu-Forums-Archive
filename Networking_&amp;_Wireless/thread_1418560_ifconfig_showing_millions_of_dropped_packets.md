---
title: "ifconfig showing millions of dropped packets"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by swm5126 on 2010-02-28
Well, with my other ethernet card problem solved, I suddenly run into this:

```
eth1
          Link encap:Ethernet  HWaddr 00:02:e3:16:37:4c  
          inet addr:10.0.2.1  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::202:e3ff:fe16:374c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294967228 overruns:0 frame:4294967228
          TX packets:0 errors:1 dropped:35 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:9 Base address:0x6000

```

This card was working perfectly fine up until....an hour ago and it started doing this. My iptables isn't blocking it somehow, because I didn't change anything. I tried reverting to an older kernel and that didn't help. It's not the network cable, it works fine in any other card.

Also, the dropped packets seem to count down? It seems to go down by exactly one every time I run ifconfig, no matter the length of time in between running it.

Ahh!

---

### Post by swm5126 on 2010-03-01
Bump.

---

### Post by chili555 on 2010-03-01
> inet addr:10.0.2.1Is this a statically set address? By any slight chance, is this accidentally the address of the router or other access point? Or is *this* the router/DHCP server?

---

### Post by iponeverything on 2010-03-01
> **swm5126 said:**
> Well, with my other ethernet card problem solved, I suddenly run into this:

```
eth1
          Link encap:Ethernet  HWaddr 00:02:e3:16:37:4c  
          inet addr:10.0.2.1  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::202:e3ff:fe16:374c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294967228 overruns:0 frame:4294967228
          TX packets:0 errors:1 dropped:35 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:9 Base address:0x6000

```

This card was working perfectly fine up until....an hour ago and it started doing this. My iptables isn't blocking it somehow, because I didn't change anything. I tried reverting to an older kernel and that didn't help. It's not the network cable, it works fine in any other card.

Also, the dropped packets seem to count down? It seems to go down by exactly one every time I run ifconfig, no matter the length of time in between running it.

Ahh!

some ideas:
- Bad card (test by going directly to another box via xover cable)
- Flaky switch (power cycle it, and try a different port)
- Bad connection, cable or end.

---

