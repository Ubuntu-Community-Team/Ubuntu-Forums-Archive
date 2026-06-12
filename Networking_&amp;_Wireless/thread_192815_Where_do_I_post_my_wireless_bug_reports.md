---
title: "Where do I post my wireless bug reports"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by fxgogo on 2006-06-09
My 3Com 3CRWE154G72 wireless card on my Compaq Armada E500 laptop is broken in Dapper as quite a few of other posts have mentioned. I want to be able to submit my findings, whether they work or not to the development crew to help them solve the issue. Is there a place I can do this? Below is a more detailed description of my problems.

My main problem is that my laptop will freeze up sporadically when I am trying to problem solve the wireless card. This only seems to happen with the islsm_pci driver. When I blacklist it and use the prism54 driver, my laptop works fine and the wireless network card get the two lights half lit, like it does when the network drivers are loaded at boot time. However when using the prisim54 driver, and I do lshw command, the network card is shown as unclaimed. I have tried most if not all of the solutions posted here to no avail.

---

### Post by awaldram on 2006-06-09
[https://wiki.ubuntu.com/ReportingBugs](https://wiki.ubuntu.com/ReportingBugs)

Yes the prism54 is borked

if you need to use it try ndiswrapper this is working for me though it really annoys me 

2 linux drivers fo rmy card have to use windows wrapper to work in dapper.

PS the prism54 in 2.6.16 works so it's dapper that bust it.

Good luck with your bug report , I'm not raising any more since they closed my last on (about dodgy kernel shouldn't be used in dapper final)

---

