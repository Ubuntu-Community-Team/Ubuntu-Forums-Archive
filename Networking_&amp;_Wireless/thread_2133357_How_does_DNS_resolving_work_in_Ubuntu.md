---
title: "How does DNS resolving work in Ubuntu?"
date: 2013-04-07
forum: Networking &amp; Wireless
---

### Post by wbar2 on 2013-04-07
I'm just curious, does anyone know how DNS resolving works in Ubuntu (I'm running 12.10)? I have changed my DNS provider in the Network Settings dialogue, and everything works fine. I'm just confused on what's cached locally and where. Specifically /etc/resolve.conf has:
```
nameserver 127.0.1.1
```
which I don't quite understand. I'd really like to get everything resolving locally, but just need some general direction on what goes on under the hood (I have searched the forum, the Web, and Ubuntu documentation, but no luck finding anything yet). Thanks! :)

---

### Post by steeldriver on 2013-04-07
I found this description quite helpful

[http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

---

### Post by wbar2 on 2013-04-07
Thanks! Finding out that dnsmasq is used helps alot. I also found that in 12.10, 127.0.0.1 in resolv.conf was changed to 127.0.1.1 which is what I have. Local caching is not done automatically, but can be enabled by adding a file to /etc/NetworkManager/dnsmasq.d/ and putting the following in it:
```
cache-size=1000
```
(1000 is the number of addresses to store). Thanks again, lots of info out there now that I know what to look for.

---

