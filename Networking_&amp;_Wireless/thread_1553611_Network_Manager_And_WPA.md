---
title: "Network Manager And WPA"
date: 2010-08-15
forum: Networking &amp; Wireless
---

### Post by Geek9 on 2010-08-15
Hello folks, been awhile since I posted, but have a general question for everyone, I'm using a Intel3945ABG wifi card and it works fairly well in windows when connecting to my wpa secured router, but rather poorly in ubuntu 10.04, now I've seen the troubles ubuntu has and I have the wpa_supplicant installed, but it still has random connection issues on my network (won't connect, keeps requesting password), to be fair the router in its self is a problem, but if I boot up in windows I can connect fine still. I've also tried using ndsiwrapper to connect, but after a so so performance I was not convinced. Anyway my question being, what's your solution to WPA woes, and should I perhaps drop the standard network manager and go for a new one?

---

### Post by NiGhtMarEs0nWax on 2010-08-15
i found WICD to be a better alternative. you will need to remove network-manager though. ps, random disconnects could be a driver or a channel issue.

---

### Post by Enissay on 2010-08-15
Same problem here, i was going to create a new thread...
I have random disconnects, and even when its connected, there's no traffic!! However, It was working fine with 9.10...
I've a Packard Bell with:
```
01:01.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
        Subsystem: Intel Corporation Device 2527
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at e0001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2
        Kernel driver in use: ipw2100
        Kernel modules: ipw2100

```
And, now i'm using a wired connection to post this...
> i found WICD to be a better alternative. you will need to remove network-manager though. ps, random disconnects could be a driver or a channel issue.
I tried it before, but still having same problem...

Thanks in advance :)

---

### Post by Geek9 on 2010-08-17
> **NiGhtMarEs0nWax said:**
> i found WICD to be a better alternative. you will need to remove network-manager though. ps, random disconnects could be a driver or a channel issue.
did even worse, tried every network manager available, prolly just the wpa/b mode issue

---

### Post by Enissay on 2010-08-18
Seems that lynx has some problems dealing with intel composants... 
I had also a problem with my intel integrated video card, ubuntu crashes when launching any video, that was fixed by installing the latest kernel : 2.6.34-020634rc7-generic
however, wireless still not working ](*,)

---

