---
title: "Transmission-daemon: lots of http connections"
date: 2012-03-09
forum: Networking &amp; Wireless
---

### Post by dstensnes on 2012-03-09
Hello.

When i start transmission-daemon, then check "netstat -napt | grep transmi | wc -l" it starts out fine, but then suddenly the connection count jumps to ~500 connections. When i configure transmission-daemon to use a proxy-server, that is where they all go, and they are indeed HTTP requests. All my peer limits are fairly low (global peer limit=100), but that doesn't apply to these HTTP connections, causing my router to suffer, and my internet to grind to a halt. I tried to use iptables to limit the amount of connections to my proxy, and that seems to do the trick. Same thing also happens without the proxy setting, however the proxy thing made it easier to create an iptables rule to limit the fallout. After a while they go away, but only with the iptables limit in place, since the internet connection would otherwise be clogged. What is transmission-daemon trying to accomplish with all of these http requests, and why on earth is it trying to do them all at the same time, completely ignoring and kind of limit?

I am using Ubuntu 11.10 AMD64 version

---

