---
title: "SSH Tunnel with 3 Hops"
date: 2011-11-15
forum: Networking &amp; Wireless
---

### Post by duiu on 2011-11-15
With some recent firewall changes out of my control, I now often need to connect to a specific webadmin page that is only connectable from a certain computer A, which can only be connected to from another server B.

Don't ask, that part is out of my control. Anyway, to get to the webadmin page I used to just port forward through A to webadmin with SSH. However, now with the firewall changes I can't get this multi-hop system to work.

Essentially I need an SSH tunnel from MyComputer -> B -> A -> Webadmin:443. How can I get this to work? (Oh, and I'm not superuser on any of these systems except MyComputer)

---

