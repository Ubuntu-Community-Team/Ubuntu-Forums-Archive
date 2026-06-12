---
title: "iptables two nic configuration?"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by maclp on 2010-07-27
hello forum-people,

i have a question regarding iptables.

here's the thing.
i have a server running ubuntu server 10.04 with 2 nic's, i want to use it to filter the internet trafic of the people in my network ussing dansguardian and squid. they both work fine.

the only problem is how to get iptables to deal with this the right way.

eth0 = LAN
eth1 = internet

can anyone please help me with this?

---

### Post by aeiah on 2010-07-27
i can point you in the right direction: look into masquerading and ip forwarding

---

