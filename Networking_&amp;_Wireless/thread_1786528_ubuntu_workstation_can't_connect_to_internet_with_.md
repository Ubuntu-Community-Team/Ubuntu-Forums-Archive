---
title: "ubuntu workstation can't connect to internet with wins server on lan"
date: 2011-06-19
forum: Networking &amp; Wireless
---

### Post by dave37 on 2011-06-19
I have 2 ubuntu file servers on our lan, primary and backup, no domain just samba and rsync, with one set as a wins server as it has improved network speed for the windows xp and vista clients.  However one ubuntu 10.04 workstation (mine) cannot connect to anything with dhcp if the wins server is set in the lan router.  I can connect, albeit slowly, with static ip.  If I disable the hybrid (point to point then broadcast) in the router and set it to "always broadcast" my workstation has no trouble at all.

Ideas please?

Thanks in advance

---

