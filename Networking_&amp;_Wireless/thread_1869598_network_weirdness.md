---
title: "network weirdness"
date: 2011-10-26
forum: Networking &amp; Wireless
---

### Post by bpexaguy on 2011-10-26
Running Nagios 3 on Ubuntu server 10.10 on moderate sized network with several locations.
Nagios ping and NSClient++ checks are fine until a remote host goes down.  When the remote host comes back up, the ping checks never work again.   Nor do pings work from the command line.
That is the real indication of the problem.   If I reboot Ubuntu, all is fine again until another server somewhere on the network dies.  Note that while ping never comes back up, NSClient++ checks do.

Tried setting Ubuntu to not accept ICMP redirects.   Then nothing came back up.

I admit my ignorance.  I have set up Nagios numerous times before and never seen this.  Was I just lucky?

Thanks.

---

