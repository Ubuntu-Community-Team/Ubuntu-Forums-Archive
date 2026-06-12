---
title: "Ndiswrapper Stopped Working"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by muenzer on 2006-06-08
Within the last few days, wireless functionality of my loptop has stopped working.  It's a broadcom card that had been connecting using ndiswrapper.  I upgraded to Dapper on June 1st, and everything worked once I switched back to ndiswrapper from bcm43xx drivers.  

I don't know if some post-release update has now broken something, or I have a hardware problem.  Need help to debug.  I've already tried starting and stoping the card using *ifup* and *ifdown*.  *iwconfig* show no ESSID or AP.

Thanks in advance.

---

### Post by ComplexNumber on 2006-06-08
i very much doubt that ndiswrapper has stopped working. it may well be that, somewhere, you've configured it to connect direct to the internet using the IP that the router had assigned *at that time. *the router may have changed the IP address assigned to you since then. the result: no more internet connection for you.
without knowing more of the background to your problem, i can only hazard at a guess. so please give some more details.

whats the contents of /etc/resolv.conf? this needs to be the address of the router.

---

### Post by muenzer on 2006-06-13
Contents of /etc/resolv.conf:

[I]search nomadix.com
nameserver 65.24.7.3
[/I]

---

