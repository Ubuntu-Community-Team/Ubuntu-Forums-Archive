---
title: "Is it necessary to edit network proxy in Ubuntu 10.04 LTS?"
date: 2011-07-06
forum: Networking &amp; Wireless
---

### Post by arroy_0209 on 2011-07-06
[SIZE=4]Can anybody please explain whether I need to set up network proxy for Ubuntu 10.04 LTS  (system->prefernces->network proxy)[/SIZE][SIZE=4]? In fact I can connect to internet using a modem without worrying about it but will it be better if I do?

In firefox, should I edit proxy setting? the options are: no proxy, auto detect proxy, use system proxy, manual proxy, and there are severl proxies like HTTP proxy etc. Does proxy setting has anything to do with security?[/SIZE]

---

### Post by jmoorse on 2011-07-12
You should not need to change the proxy settings.  It will not make it 'better'.

Proxies are used to 'intercept' and forward requests, often for HTTP/S.  Many companies use this for caching and content filtering.

You can also use a proxy to hide the origin of your request (eg: your IP) to a remote web server.  I recommend you Google web proxy if you want more info.

---

