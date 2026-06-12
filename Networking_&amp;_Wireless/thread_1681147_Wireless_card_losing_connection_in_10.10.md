---
title: "Wireless card losing connection in 10.10"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by cduston on 2011-02-03
Hey all, 

   Got a new comp, running 10.10 (64 bit - according to the About Ubuntu it's actually 11.04?) and I'm having some trouble with my wireless card dropping it's connection. It seems to happen randomly, and even relogging doesn't make it come back. A complete restart restores all functionality. It takes 10-60 minutes for it to lose contact with the Router. It can still see the network but just goes into infinite "try and connect" loop. 


Here's some info (ask for more, not sure exactly what will help)
```

lspci -v 

0a:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
        Subsystem: D-Link System Inc Device 3a70
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at f7ef0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k
        Kernel modules: ath9k

```If it matters, my Windows 7 64-bit works fine with the card. Is this maybe a driver problem, or some 64-bit compatibility? Been looking around but don't have much experience debugging networks.

Any help will be appreciated, thanks!

---

