---
title: "resolv.conf.tmp Where'd that tmp come from?"
date: 2012-05-18
forum: Networking &amp; Wireless
---

### Post by elgordodude on 2012-05-18
The system is a Lubuntu 11.10 live drive installation on a 16 gig USB 2.0 stick that I move around to take care of viruses and data recovery and such.

On the current box it's wired to a repeater which connects wirelessly to an AP. Connectivity is good I get a DHCP address of 192.168.1.5 and can ping the router and 8.8.8.8

However I cannot connect to a web page or the ubuntu servers which led me to think it was a DNS error. A trip through /etc reveals that the resolve.conf file is now named resolv.conf.tmp Hmmm, so I tried to rename it and received an I/O error, so I tried to reinstall resolvconf but of course both apt-get and synaptic rely on DNS.

The resolv.conf.tmp file itself is fine, it points to my router, openDNS, and googleDNS, and I'm becoming increasingly convinced that little .tmp is fouling up the works, so to get back to the title where'd that .tmp come from?

---

