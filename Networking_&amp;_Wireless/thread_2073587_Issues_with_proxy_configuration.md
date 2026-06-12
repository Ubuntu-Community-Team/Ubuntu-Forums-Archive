---
title: "Issues with proxy configuration"
date: 2012-10-19
forum: Networking &amp; Wireless
---

### Post by Q8root on 2012-10-19
Hello ,
I have setup http proxy in chrome , Now when i disabled the proxy in the chrome in terminal the proxy is still working .
```
ahmad@ahmad:~$ wget http://masar-kw.com/test.rar
--2012-10-20 04:43:28--  http://masar-kw.com/test.rar
Resolving server.q8.com (server.q8.com)... 213.72.190.18
Connecting to server.q8.com (server.q8.com)|213.72.190.18|:1344... connected.
Proxy request sent, awaiting response... ^C
ahmad@ahmad:~$ 

```

How can i completely disable the proxy ?

---

### Post by efflandt on 2012-10-20
Are you at a school or community college in Sidney?  They own that 213.72.190.18 IP  Maybe they have a transparent proxy that you cannot control (so watch what you do).

I get a different IP (in Belgium) for server.q8.com:

efflandt@XPS8100-1204:~$ **host server.q8.com**
server.q8.com has address 178.208.36.141
server.q8.com mail is handled by 0 kpvm.q8.nl.

---

