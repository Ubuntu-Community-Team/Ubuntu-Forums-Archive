---
title: "Creating a Proxy Server w/Ubuntu 10.04"
date: 2010-06-28
forum: Networking &amp; Wireless
---

### Post by justinmiller87 on 2010-06-28
Hello all.

Recently at work, they decided to block a wonderful site I used to access all day long (Facebook) so I'd like to be able to setup a proxy server on my Ubuntu box in order to access it from here as they wisely block all the other sites that allow one to proxy. What is the best one to do, and what would I need to do in order to be able to access it from an external IP, to include unlocking what ports on my wireless router?

Any help would be greatly appreciated, so thanks in advance.

---

### Post by nixscripter on 2010-06-29
Disclaimer: I do not take any responsibilty for any trouble you get into, be it legal or moral.

The best [transparent proxy]("http://en.wikipedia.org/wiki/Proxy_server#Transparent_and_non-transparent_proxy_server") server that is open source is Squid.

[http://www.squid-cache.org/](http://www.squid-cache.org/)

It is available from the Ubuntu repository. Install this on a computer you can control that faces the internet, and point your browser to this as the proxy (in the preferences).

I would also add: many corporate firewalls block other proxies. It's pretty easy to detect.

---

