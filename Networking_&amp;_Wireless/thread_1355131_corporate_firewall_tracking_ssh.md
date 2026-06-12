---
title: "corporate firewall tracking ssh"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by alladnsane on 2009-12-14
Just curious as to the tracking abilities of corporate firewalls.  My work has an intranet as well as internet access. It spans several physical locations.  If I ssh from there to my home network how likely is it that my outgoing connection would be detected and/or traced to my home ip by their firewall?? And is there any way for this not to happen ie. ssh out through their system without alerting them that i am tunnelling through their firewall.  For the record, I am not doing anything technically wrong, just want to make use of some of some free time at work to config my home server (i don't seem to have time to administer to it while at home), and my employer doesn't have the most liberal policy when it comes to IT policy.

Thank-you

---

### Post by paulisdead on 2009-12-14
It depends on how closely they're watching.  I doubt they're doing much more than watching ports and connection states, but it's possible they're doing more.  I think the easiest way would be to run ssh on a different port, like port 80 or 443, so it looks like web traffic.  Though they might require that sort of traffic to pass through a proxy on their network, so those might be out.  It'd then be a matter of figuring out a port for some generic type of traffic they allow out, and set up your home ssh server to run on that port.

Also, I'm sure doing this is against their network use policy, and if caught, could be grounds for termination.  But, hey, it's your job.

---

### Post by cariboo on 2009-12-14
The easiest way to solve this issue is to talk to the IT department and find out what the policy is. 

It is against forum policy to help you circumvent restrictions in the workplace. Thread closed.

---

