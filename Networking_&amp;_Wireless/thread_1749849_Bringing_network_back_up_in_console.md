---
title: "Bringing network back up in console"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by NSDragon on 2011-05-04
Hello,

I recently installed 11.04 on an older laptop to use as a server via wireless network, got ssh and apache/mysql and all that jazz, disabled gdm and tested on my local network and it worked just fine.

However after a while I discovered that after a while wlan0 just died and I couldn't get to my server at all. I had to locally run ```
ifup wlan0
``` to bring it up again. I've looked about the reason why wlan0 kept going down seemingly at random but couldn't find anything.

So I'm wondering... I could just stick a script that runs "ifup wlan0" in /etc/network/if-down.d/ but I don't know about any possible side-effects, and I'm thinking there must be a better way--short of solving the root cause of it, which I'm looking into, but this would be a stopgap measure.

Can anyone help me out on this?

---

