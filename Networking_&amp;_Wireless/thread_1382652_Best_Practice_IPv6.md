---
title: "Best Practice: IPv6"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by williamburn on 2010-01-16
I am curious what the best practice is for IPv6 and its connectivity.  After a new install, should it be disabled or enabled.  From a security standpoint, doing some tcpdumps on the interface, it appears that traffic is indeed present.  

Thanks

---

### Post by puppywhacker on 2010-01-16
I love IPv6. I am sad to see recommendations to disable it. We had 10 years of time to embrace it and learn how to use it properly, because there are a multitude of benefits, but nobody seems to care.

By default a link has a "link-local" address which starts with fe80:: so all nodes are by default capable of communicating to the other nodes on the link without any configuration. Also it is easy to add multiple addresses to one interface. In my internal network I use addresses from the site-local range "fec0::" and I use a sixxs as a tunnel broker for my IPv6 public addresses.

Since most providers don't use IPv6 your IPv6 addresses can't be reached from the internet. Everything in your internal network can use a mixIPv6 or IPv4  the biggest security related issue is that if you use iptables to drop certain ports you should need a matching rule in ip6tables

---

### Post by Miko_UK on 2010-01-26
I Don't think it's the users who don't want to use IPV6
If your ISP can't handle it or your modem/router won't take it then you have no option but to disable it.
In my case the manufacturers of my modem (Netgear) refuse to release a firmware patch as they no "longer support it" for that you could read *"As it's over a week old we can't be bothered to write a patch as there's no money in it for us but if you want IPV6 just buy a fresh modem and we'll be $£€ richer"*
Ubuntu should be *praised* for including IPV6 as default and *castigated* for not making it easy to turn of when things go pear shaped. Especially as you can't search for how to disable it if your intrernet ain't working

---

### Post by Skaperen on 2010-02-02
If you don't have a router with IPv6 nearby, then there should be no need to disable IPv6. I have never seen it interfere with IPv4 functionality. OTOH, if your network does have global IPv6, there are benefits. For example, you can (for now) skip the spam testing on email arriving over SMTP on IPv6. You'll know when IPv6 is ready for prime time when the spammers use it (FYI, many porn and warez sites already do).

---

