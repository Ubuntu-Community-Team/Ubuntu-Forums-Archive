---
title: "ifupdown query"
date: 2009-08-21
forum: Networking &amp; Wireless
---

### Post by misio129 on 2009-08-21
hey,

i had a networking problem where all the connections in network manager were shown to be disconnected. By changing 'managed=false' to true in /etc/NetworkManager/nm-system-settings.conf, I solved the problem. this gave me two new connections though, ifupdown(eth0) and ifupdown(eth1). i was just wondering if someone could tell me what these were and to what they refer to?

cheers.

---

### Post by Brandon Williams on 2009-08-22
There's a file called /etc/network/interfaces in which you can define network interface configuration settings. If you add configure your interfaces there, then they will typically not be managed by NetworkManager. In fact, they won't even show up in the NetworkManager guis (e.g. the status try icon will not show them). However, if you change that setting to 'true', then interfaces defined in /etc/network/interfaces _will_ be managed by NetworkManager and they will show up in the guis. If ones marked ifupdown are the items from /etc/network/interfaces.

---

### Post by p1977p on 2009-08-24
i had the same problem. Can I rename the ifupdown (eth0) {in my case} to something else?

---

