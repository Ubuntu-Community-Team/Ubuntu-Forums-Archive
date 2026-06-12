---
title: "Making stuff work behind Authenticated proxy"
date: 2013-02-05
forum: Networking &amp; Wireless
---

### Post by cyanide911 on 2013-02-05
I'm posting this from behind my college's authenticated HTTP proxy network. I'm not sure what kind of proxy it is exactly, if there's a way to find out do let me know.

Now I'm having a lot of trouble getting some things like git clone, pip etc. working on this network. I presume that's because they work with regular proxies but not authenticated proxies.

There must be a way to get such components to work, but I can't figure out how to, even after googling for hours and hours. 
I did find out about CNTLM, which acts as a proxy-proxy and will eliminate such  program's need to interact with an auth proxy and instead I can simply direct them to a localhost IP as a proxy.

But I cannot get CNTLM to work. So yeah either
a) Please help me get CNTLM to work
b) Do tell me any other way to get such components working behind authenticated proxies.


For a), I cannot figure out how to fill the config file. My proxy is of the form > [http://user:](http://user:) password@proxyserver:8080What am I supposed to fill in these fields:
> Username 
Domain        
Password 
Proxy
Proxyusername and password are obvious. Proxy I presume would be proxyserver:8080. What about Domain?




Ubuntu 12.04

---

