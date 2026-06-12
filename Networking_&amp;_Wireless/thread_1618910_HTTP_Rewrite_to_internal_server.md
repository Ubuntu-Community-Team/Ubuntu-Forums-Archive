---
title: "HTTP Rewrite to internal server"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by lynwode on 2010-11-11
Hi Guys,

Here is the scenario. I have a registered domain that resolves (via dyndns) xxx.mydomain.com to my external facing router -easy no issues there. Behind the router I have several machines (some VMs) running webservers, mail etc... What I want to be able to do is redirect the external traffic based on xxx to the relevant internal machine and serve the content back to the external world.

I have tried using a http rewrite of xxx.mydomain.com to the relevant machine an it works fine from within my network, however externally the re-direct fails as the master DNS servers have no record of internal DNS setup in my network (obviously). 

So is there anything I can do to get xxx. recognized externally? I'm only just starting to get my head around how DNS, HTTP, TCP etc all hang together. Am I barking up the wrong tree with rewrite? Should I be looking at proxys? Any pointer would be appreciated.

Cheers,
Tim.

---

### Post by lynwode on 2010-11-11
Ok looks like I have answered my own question - a reverse proxy seems to be the way forward. 

Gonna be a fun evening working this one out.

---

