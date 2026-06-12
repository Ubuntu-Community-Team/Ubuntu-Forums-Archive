---
title: "run cups over apache"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by wasutton3 on 2009-08-31
Ok, i have a bunch of services running over a bunch of different ports, CUPS, transmission, etc. I would like to have them all running under port 80 on my apache server. I have transmission working, but when i try to use my router admin page and CUPS, they appear but none of the graphics seem to follow. My config is listed below for cups, the router admin config is almost identical. Did i leave something out? am i on the right track? thanks in advance

```
#Cups forwarding
    ProxyPass /cups http://localhost:631
    ProxyPassReverse /cups http://localhost:631
#End Cups forwarding

```

---

