---
title: "ubunut10.04 can't connect to wireless router"
date: 2011-04-14
forum: Networking &amp; Wireless
---

### Post by ammon on 2011-04-14
I have been using pppoe connect to Internet,now I want my notebook get on line,I bought a wireless router but Ubuntu(64-bite) can't connect to Internet through the wireless router.pppoeconf said that found eth0 and vboxnet0,but search concentrator failed and pppoeconf exited.How can I fix it.Thanks a lot.

---

### Post by ammon on 2011-04-15
I fixed the issue by deleting /etc/ppp/peers and /etc/NetworkManager/nm-system-settings.conf managed=true.OK!

---

