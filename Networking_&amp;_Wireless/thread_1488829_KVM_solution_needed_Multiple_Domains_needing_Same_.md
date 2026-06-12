---
title: "KVM solution needed: Multiple Domains needing Same Network Data"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by mattlal on 2010-05-20
I have an interesting configuration question and trying to find if  someone can help me out determine the best solution:

Basically, I  have a KVM configuration with some guests that are looking for the same  UDP/Syslog traffic.

I do not want to interfere the integrity of  the message, so I would like to duplicate the traffic to all the guests  on the KVM host using iptables or something similar. 

I believe  there might be ways to use rsyslog, but I haven't had great success  forwarding to standard syslog listening guests, but may be my only  solution.

Any help would be greatly appreciated.

---

