---
title: "Xorg using a lot of memory"
date: 2012-06-10
forum: Multimedia Software
---

### Post by tarahmarie on 2012-06-10
Hi, all:

Kubuntu 12.04
Nvidia GeForce GT430 (using proprietary drivers)
8GB RAM

For about two weeks, I've been seeing some crazy spikes in RAM usage; a 'ps aux --sort -rss' gives this as the top process:


root      1153 18.1 12.2 1134664 996764 tty7   Rs+  Jun05 1089:31 /usr/bin/X :0 vt7 -br -nolisten tcp -auth /var/run/xauth/A:0-aCxRga

So, it's something to do with X, obviously; I am not a graphics/hardware person, so I don't know where to dig in to find the problem. I can't simply kill the process; I need to find out why this is happening. Searching around, I see someone who may be having a similar problem to mine, but I'm not sure: [https://forums.virtualbox.org/viewtopic.php?f=3&t=49820](https://forums.virtualbox.org/viewtopic.php?f=3&t=49820)

Can I get some tips on where to start looking?

---

