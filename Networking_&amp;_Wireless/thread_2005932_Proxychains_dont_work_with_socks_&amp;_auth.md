---
title: "Proxychains dont work with socks &amp; auth"
date: 2012-06-18
forum: Networking &amp; Wireless
---

### Post by tabstop on 2012-06-18
i would like to use a socks5 proxy (with authentication) with some programs. I found proxychains. I installed this and added my proxyIP,port,user and pw to /etc/proxychains.conf. A test like "proxychains wget google.com" failed (timeout)

proxychains wget google.com ProxyChains-3.1 ([http://proxychains.sf.net](http://proxychains.sf.net)) --2012-06-18 17:15:37-- [http://google.com/](http://google.com/) Auflösen des Hostnamen »google.com«... 173.194.70.100, 173.194.70.101, 173.194.70.102, ... Verbindungsaufbau zu google.com|173.194.70.100|:80... |S-chain|-<>-94.x.x.x:999-<><>-173.194.70.100:80-<--timeout

The proxy works. I tested with proxyfire in winXP. What is the problem? Did i forget something? Do you know an alternative?

---

### Post by tabstop on 2012-06-20
perhaps anybody find the problem in my /etc/proxychains.conf

[http://pastie.org/private/tugikvp66nwd5diku1yua](http://pastie.org/private/tugikvp66nwd5diku1yua)

---

