---
title: "strange wireless behavior?"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by moore.bryan on 2009-08-03
I'm working on a Lenovo z61e Thinkpad, running Jaunty and the 2.6.31-020631rc5-generic kernel. Usually, I simply use /etc/network/interfaces to connect with my home and work networks, which are WPA2 and WEP protected, respectively; for any other connections, I've been using network-config. I'm currently camping in the Adirondack state park and the campground in which I'm tenting has WiFi. When I got here, I tried using my go-to method without success... network-config could *see* the unsecured public network, but couldn't connect. I used a thumbdrive and my wife's XP laptop to get wicd, installed it, and now no problems connecting. It's a temporary fix, but one which bothers me. Why can wicd see *and* connect to a network, but editing the /etc/network/interfaces file, using network-config, *and* trying to manually connect through iwconfig can't?

---

