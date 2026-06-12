---
title: "Load-balancing multiple DSL connections"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by el3ktro on 2006-06-12
Hello, I hope you can help me a little. Currently the office I'm working in has 4 different Internet DSL gateways for ~80 client machines. 20 clients use gateway 1, 20 use gateway 2 and so on. This is a working, but inefficient solution. I'm searching for a way to do some load balancing between these four DSL connections. I want to configure all clients to use _one_ standard gateway, and this gateway dynamically routes all Internet traffic to one of the four DSL routers. It would be cool for all kind of traffic, but it would be okay if it is only for HTTP/FTP. Is there any way to do this with an intermediate Linux machine (sitting between the clients and the four DSL routers)?

Tom

---

### Post by Chuckaluphagus on 2006-06-24
I'd be interested in this as well. <bump>

---

### Post by mips on 2006-06-25
Try this [http://tetro.net/misc/multilink.html](http://tetro.net/misc/multilink.html)

or google **Linux multilink**

---

