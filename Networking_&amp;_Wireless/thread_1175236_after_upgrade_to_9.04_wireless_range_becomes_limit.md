---
title: "after upgrade to 9.04 wireless range becomes limited"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by sebastianrimbaud on 2009-05-31
I have an emachines d620 laptop with built-in wireless and upgraded from 8.10 to 9.04

Beforehand, my wireless worked fine. After the update I noticed my wireless didn't work like it used to from my room.

I started to realize only when I was close to the router, did my internet start to work.

I haven't tested it anywhere else outside my home.

It can't be my router, we have a desktop with kubuntu, and another laptop in the house with ubuntu and all have been updated. 

However, kubuntu is running wicd instead of network-manager. I tried wicd and replaced the network-manager, but so far I'm at a loss. 

Any ideas on what may be wrong?

---

### Post by coffeeaddict22 on 2009-06-01
A lot of wireless drivers got added to the kernel with the last couple of versions- which means if your card was on ndiswrapper, you'll have a conflicting driver there now.  Type ```
lspci -v
``` nto a terminal and post back the output if you need more help.

---

