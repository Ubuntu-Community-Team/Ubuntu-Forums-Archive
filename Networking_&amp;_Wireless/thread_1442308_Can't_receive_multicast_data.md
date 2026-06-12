---
title: "Can't receive multicast data"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by AstroCityKubus on 2010-03-29
I'm working on an app to view data from various multicast servers/services.  I've written a simple one where all it does is take parameters of interface ip, multicast address and port and then just dump the data out as it comes in to stdout.

I can see that I'm sending the proper igmp join out(my network is igmp_v2 and I've verified my joins are as well) and that I'm getting data in on the appropriate interface through tcpdump, but I'm not getting any data on the app through the recvfrom() method.

I've compiled this on various other distros (RHEL 5.4, Gentoo, Ubuntu 9.10, etc) and it works like a charm there - but nothin on Ubuntu 8.04.
I'm completely stumped by this - any ideas on what it could be?  Any advice would be helpful at this point.

Oh, one more thing - this seems to be confined to recvfrom() as I can run a simple multicast messenger service on this server and the other systems will receive the messages perfectly.

Thanks in advance for any and all help.

---

