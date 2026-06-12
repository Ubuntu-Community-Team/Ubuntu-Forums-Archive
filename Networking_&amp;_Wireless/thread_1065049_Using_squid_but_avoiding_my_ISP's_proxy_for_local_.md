---
title: "Using squid but avoiding my ISP's proxy for local files"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by scottishnarn on 2009-02-09
Hi,

I'm running a squid proxy server with squid guard at my school to block certain websites that are not blocked by our local education authorities proxy. (We have to go through their proxy to access the internet.) 

Following the squid user guide I use the following (with our proxy server) to force access through our LEA's proxy.

```
cache_peer cache.myisp.example parent 3128 3130 default no-query
```However, we also need to access some local network web pages and this won't work through the proxy. Is there a way of configuring squid so all internet traffic is routed through the LEA's proxy but local traffic is not?

Thanks.
David

---

### Post by scottishnarn on 2009-02-10
bump

---

### Post by scottishnarn on 2009-02-10
OK, I figured it out. I had to add the following lines to my /etc/squid/squid.conf file
```
acl localweb dstdomain local-ip
always_direct allow localweb
```
where local-ip is the ip address of our local web server (which only needs to be accessed by ip).

---

