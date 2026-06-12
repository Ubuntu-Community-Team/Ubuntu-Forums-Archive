---
title: "After 8.10 can't see pc on network when wirelessly connected"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by thomaswp on 2008-12-28
I have a squeezebox - basically a tiny PC that streams music from my laptop.  When on 8.04 I could run my music server on either wireless OR wired connection.  Since the update to 8.10 I now find I can only run it on a wired connection.

I had a look at iptables and allowed access on tcp/udp on port 3483 and tcp on port 9000 - which is all that the squeezebox needs.  I thought I was getting somewhere, since this allowed intermittent connections from the squeezebox to my laptop on wireless.  But the connection was by no means stable.

So I wonder if:

a) 8.10 has made the wireless unstable (no idea where to check the logs on this but browsing is absolutely fine)
b) there is some weird firewalling issue I cannot fathom in Intrepid...

---

