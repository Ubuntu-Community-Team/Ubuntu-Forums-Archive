---
title: "Ubuntu Natty as Virtual Machine - performance problem"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Nial6 on 2011-04-03
Hi all. I'm using 'minimalist' (build with mini-cd install) Ubuntu 10.10 as Virtual Machine with Hyper-V. I'm using Staging Drivers (Microsoft Integration Services) for Hyper-V virtual network card. To do this, I have to manually upgrade kernel to 2.6.38 (older ones have problems with Hyper-V network adapter drivers - errors like 'scheduling while atomic', and other problems). On Ubuntu 10.10 with 2.6.38, I can get tansfers, about, 1.3GB/s (1Gb/s). But on Ubuntu Natty, which is also 2.6.38, I can get only half of that - max 500MB/s. I got the same problem on SuSE Linux with 2.6.37 - transfers max 500MB/s, but I thought it's problem with 2.6.37. I thought that 2.6.38 kernel finally uses Hyper-V virtual network drivers well. 

What's wrong with Natty? Or I have to search for specific version of 2.6.38 to get the correct speed? Or maybe it's not the problem with kernel, but problem with Natty which consumes too many CPU?

EDIT: sorry for my bad english.

---

