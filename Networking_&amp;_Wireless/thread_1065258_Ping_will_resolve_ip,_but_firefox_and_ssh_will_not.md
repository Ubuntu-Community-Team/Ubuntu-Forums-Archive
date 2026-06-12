---
title: "Ping will resolve ip, but firefox and ssh will not"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by diginux on 2009-02-09
I just upgraded today to Jaunty. Upon doing so, I can no longer resolve IP addresses with ssh, firefox, etc. I however can resolve hostnames, like ping google.com and host google.com work just fine. However if I try to goto google.com in the web browser, it says it can't not resolve the address. If I try to ssh somewhere it also says unknown host.

I have tried editing /etc/nsswitch.conf to be

hosts:        files, dns

But that did not help. I also tried booting into rescue mode with networking, but that didn't help either.

I am now stuck and looking for help. Thanks!
JW

---

### Post by diginux on 2009-02-09
So I figured out the problem. It appears Ubuntu(Jaunty) is trying to use ipv6 and my dns does not support ipv6. So now I need to figure out how to force it to use ipv4 for everything.

---

