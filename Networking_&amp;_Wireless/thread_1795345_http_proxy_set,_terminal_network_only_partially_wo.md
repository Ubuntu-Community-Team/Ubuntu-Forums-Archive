---
title: "http_proxy set, terminal network only partially working"
date: 2011-07-02
forum: Networking &amp; Wireless
---

### Post by brianfernandes on 2011-07-02
I'm using Ubuntu 10.10, Desktop edition. Using a proxy which is set for all protocols under the  Preferences > Network Proxy configuration, Firefox and Chrome work  just fine. I have set Firefox to use "System proxy settings". Ubuntu is  even seeing package updates.

The proxy setting was applied system  wide and when I open my terminal and try "echo $http_proxy" I see the  same proxy as expected - http://<proxyip>:3128 . However,  ping/ssh/links won't work. If I specify the domain in those commands, I  get an "unknown host" error. If I use the IP directly, I get a "no route  to host" error. At the same time, running apt-get from the terminal  still works. 

Any ideas where things are going south? 

Thanks,
Brian.

---

