---
title: "Linux AFP File Server Speed"
date: 2012-07-19
forum: Networking &amp; Wireless
---

### Post by linuxheadaches on 2012-07-19
Good Day All,

A while back I made an Ubuntu 12.04 server that acts as a file server. This file server takes a beating. I have it configured with a Intel 82580 4 port nic. There are two Adaptec 6805 controllers that control 16 2TB drives. I have four Mac OS X 10.7 workstations that each access it over their own dedicated port. So far it has handled about everything I have thrown at it. But now they want to start pushing 1080p video for editing... It works ok on playback, and 1.5x and 2x scrubbing, but anything faster than that it starts to choke...

My question, how do I make connections faster? I can add in additional NIC's to both the server and the workstations. I would like to have ~3Gbps for each system. I am trying to stay away from Fiber channel due to the high associated costs. Is there anyway to "bond" (I know that bonding is not the route to take, but a similar function, like iSCSI or something) the interfaces together to get a higher throughput?

Thanks!

---

