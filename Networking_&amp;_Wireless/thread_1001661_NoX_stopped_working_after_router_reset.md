---
title: "NoX stopped working after router reset"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by pickarooney on 2008-12-04
I had to reset my router the other week and since then NoX (noMachine) is not working from remote locations. 
I enabled DynDNS on the router and opened port 23 to the NoX server on my desktop. Then I noticed the client was trying to connect to port 22, so I opened that instead. 

Still no joy. 

I know this is some simple thing but I can't find decent documentation on it.


edit: When I telnet port 22 on my router's external IP from a remote location it fails instantly, instead of taking 30 seconds the way it fails if I telnet an unopened port.

---

