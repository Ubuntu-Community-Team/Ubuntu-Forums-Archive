---
title: "What is causing this in firefox? Worked fine in breezy"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by Whimar on 2006-06-02
Hi there,

new to the forums here,

I've just upgraded to dapper, and i find that firefox is taking a long time to "look up" address's.  It never resonded this way in breezy, it was very very quick at resolving the domain.  

I dont know if this is related, but my network card wasnt enabled by default when i logged into dapper for the first time like it was when i logged into breezy.  I'm using a DFI nf4 sli-dr motherboard, and running the integrated yukon controller as my NIC.

Any help would be greatly appreciated.

Thanks!

---

### Post by Whimar on 2006-06-02
Solved the issue, seems to be related to ipv6 not supported on my router. 

Basically i just typed about:config into firefox, then filtered for:

network.dns.disableipv6

and set it to true.  Problem resolved.

---

### Post by kostkon on 2006-06-02
[QUOTE=Whimar]Solved the issue, seems to be related to ipv6 not supported on my router. 

Basically i just typed about:config into firefox, then filtered for:

network.dns.disableipv6

and set it to true.  Problem resolved.[/QUOTE]

Yeah, that's seems to be a common problem. In general, when you disable ipv6 in Firefox you get better lookup speeds.

---

