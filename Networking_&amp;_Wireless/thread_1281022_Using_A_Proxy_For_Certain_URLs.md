---
title: "Using A Proxy For Certain URLs"
date: 2009-10-02
forum: Networking &amp; Wireless
---

### Post by tablebreaker on 2009-10-02
Hey all,
There are a couple of exact URLs that I want to have going through a proxy when requested, via web browser or terminal. I'm looking for something similar to FoxyProxy for Firefox, but universal. Is it possible to set a proxy IP address for certain URLs in the hosts file?

Thanks!

---

### Post by kidders on 2009-10-04
Hi there,

Unfortunately not. The URL being requested by an application only comes into play after the connection has been initiated, so by the time you discover what it is, it's too late to re-route the connection.

---

### Post by wilee-nilee on 2009-10-04
[http://www.torproject.org/](http://www.torproject.org/)

---

### Post by tablebreaker on 2009-10-04
Thanks for the replies, guys. I know about TOR already, but I'm not sure how to use it as a command line app-wrapper. I'll try to contact the developer of FoxyProxy to see if he has any ideas for how to apply it towards all network connections, not just those inside foxyproxy

---

