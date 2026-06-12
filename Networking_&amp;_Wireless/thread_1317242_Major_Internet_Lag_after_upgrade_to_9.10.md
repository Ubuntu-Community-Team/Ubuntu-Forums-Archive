---
title: "Major Internet Lag after upgrade to 9.10"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by crazy dave on 2009-11-06
Can anyone advise if they've experienced lags with webpage impressions after upgrading to 9.10. I have major delays, and have tested Firefox, Opera, and Epiphany, all with the same result; there is a significant delay in loading fresh webpages, either through clicking on links, clicking bookmarks, or through searches. This is not a problem with the ISP as other PC's and devices do not suffer this problem. Also ADSL speedtests show all is fine.

I've read some threads suggesting it might be IPV6, does anyone know for sur

---

### Post by Freedom65 on 2009-11-06
I had the same problem and switched from network manager to wcid and that fixed it.You can download it from synaptic.;)

---

### Post by crazy dave on 2009-11-06
thanks but that hasn't helped. No improvement,

---

### Post by Freedom65 on 2009-11-06
I had to shutdown completely and restart to see the improvement.Don't know if that will help you any,but mine was slow with wicd till I did that.:D

---

### Post by crazy dave on 2009-11-06
thanks but that hasn't helped. No improvement,

---

### Post by crazy dave on 2009-11-06
_**OK thats fixed it**_ Thanks a lot everyone. I inserted the DNS Servers with those from my routers firmware as advised and its done the trick. Many **Thanks.**

heres the workaround as supplied to me;

> Quote:
Originally Posted by PhilGil View Post
There is a large thread in Launchpad about this problem: [https://bugs.launchpad.net/bugs/417757](https://bugs.launchpad.net/bugs/417757)

My layman's understanding of the bug is that Karmic's DNS resolver tries to do an IPv6 lookup before IPv4. If your modem/router is not configured to respond to the IPv6 request the resolver has to wait until the query times out, causing the delay.

There's talk in the thread about a patch, but in the interim what has worked for me is to bypass my router when doing DNS lookups. I have had success using DNS servers from my ISP as well as Open DNS. Instructions for manually entering a primary and secondary DNS server are here (these are instructions for Open DNS, but should work for your ISP's DNS server - if you know the IP addresses): [https://store.opendns.com/setup/operatingsystem/ubuntu](https://store.opendns.com/setup/operatingsystem/ubuntu)

---

