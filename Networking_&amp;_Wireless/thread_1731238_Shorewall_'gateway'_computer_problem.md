---
title: "Shorewall 'gateway' computer problem"
date: 2011-04-16
forum: Networking &amp; Wireless
---

### Post by espressobeanie on 2011-04-16
I have a bit of an issue with shorewall. I overwrote my NAT configure files, and I can't seem to figure out how to make NAT work again on two ethernet cards (eth0 and eth1). eth0 connects to the ISP and eth1 connects to my Local LAN. They're defined in the interfaces, and I can ping DNS Masq from my Win7 computer, but I can't figure out how to get eth1 traffic forwarded to eth0 without knocking eth0 traffic offline (ProxyARP failed that for me). 

Is there anyone who's expert on Shorewall who might take a look? It's driving me nuts.

---

