---
title: "Squid parent cache question"
date: 2011-11-10
forum: Networking &amp; Wireless
---

### Post by albanderuaz on 2011-11-10
Hi all,

I have two squids linked together, SQ1 pointing to SQ2. Proxy settings of local internet browsers are pointing to SQ1. The internet works fine.

I would like to ask SQ1 not to forward any request whose destination is let's say 10.11.12.13 to its parent cache, and hence to prefer a direct connection.
I have put in SQ1's squid.conf:

> cache_peer proxy.domain.com parent 3128 0 deny all
acl ip dst 10.11.12.13
always_direct allow ip
never_direct allow allThe internet is still working, but when I try to access [http://10.11.12.13](http://10.11.12.13) from a PC, the connection times out and it is written in SQ1's :

> (time) (packet size) (incoming ip) TCP_SWAPFAIL_MISS/000 0 GET [http://10.11.12.13/](http://10.11.12.13/) - FIRST_UP_PARENT/proxy.domain.com -Now why is it written FIRST_UP_PARENT? Is something wrong with the way I use always_direct?


If I remove the 4 lines, I can browse to 10.11.12.13 but the internet no longer works (which is normal as SQ2 has the internet access)

Thank you for your help!

---

### Post by albanderuaz on 2011-11-10
Ok, if I change the acl by putting the source of the packet instead:

> cache_peer proxy.domain.com parent 3128 0 deny all
acl ip src 10.11.12.14
always_direct allow ip
never_direct allow all                      I can access my intranet web browser (on 10.11.12.14) but I can no longer access the external internet. It seems like Squid does not manage to compare the destination IP of the packet to 10.11.12.13, how come?

---

### Post by albanderuaz on 2011-11-10
Ok, so I have replaced the acl, now I check the content of the URL with the acl. It finally works.

---

