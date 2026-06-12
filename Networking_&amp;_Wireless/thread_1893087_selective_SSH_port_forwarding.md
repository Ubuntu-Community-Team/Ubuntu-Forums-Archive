---
title: "selective SSH port forwarding"
date: 2011-12-09
forum: Networking &amp; Wireless
---

### Post by tbastian on 2011-12-09
I realise the following may sound a little bit shady, but I assure you all parties involved have given their express consent.

I work in the same building as my father, and he has gotten IT to open up ssh ports so he can log into his machine and work from home.

Since I'm only going to be working there for a few more months, instead of getting IT to go through all this trouble for me, I'd just like to set up port forwarding on his machine to my machine. (so I can log into my machine without the extra step of logging into his machine first)

Is it possible to port forward automatically, but only if I try to log in from a certain username? ie: can I set it up so that he can log in normally to his account, but I can log into my machine directly?

---

### Post by Lars Noodén on 2011-12-09
That would be using your father's machine as a jump host. I've put some of my notes on [jump hosts](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Proxies_and_Jump_Hosts#Jump_Hosts_--_Passing_through_a_gateway_or_two) online, but searching around you can find better descriptions and HowTos.

---

