---
title: "Network machine name"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by brevleq on 2010-03-15
Hi guys, I'm creating a pentaho application using glassfish and now I want to test it in another machine, so I've tried put this in firefox of windows machine: "geotech97:21897/pentaho" but the windows machine can't find geotech97 machine.
If I put the ip it find well but pentaho is configured to use geotech97 domain.
My question is: how can I access my application running on linux computer in another computers just using linux machine name??

Thanks for your attention

---

### Post by estamand on 2010-03-15
Edit your hosts file (C:\Windows\System32\drivers\etc\hosts) to map your network name to the machine's IP.

---

