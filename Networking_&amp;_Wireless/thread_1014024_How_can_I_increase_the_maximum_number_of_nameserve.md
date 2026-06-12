---
title: "How can I increase the maximum number of nameservers?"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by tep47 on 2008-12-17
Hi, I'd like to know how to increase the maximum number of nameservers used by resolver.  According to the manpage for resolv.conf the maximum is 3, as defined by MAXNS in <resolv.h>.  I changed the value in that file, but obviously it didn't work (I assume I'd have to recompile resolver).

I'd like to increase this limit because the VPN client I use inserts 4 nameservers in /etc/resolv.conf.  I run my own nameserver on my home network.  My own nameserver ends up last in the list, and doesn't get used, so I can't resolve names in my home address.  Any help is appreciated.  Thanks.

(oh, I'm running Ubuntu 8.10 on a T60p Thinkpad, if that matters).

---

### Post by zika on 2008-12-17
I have 7 nameserver entries in /etc/resolv.conf. I am not sure if they are all accepted by resolver but they are there. what is the right way to check how many of them are 'in use' ...?

---

