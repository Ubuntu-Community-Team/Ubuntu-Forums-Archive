---
title: "How to ssh tunnel to a computer that uses proxy"
date: 2012-04-21
forum: Networking &amp; Wireless
---

### Post by rajun198 on 2012-04-21
I am on computer C1
created a dynamic ssh tunnel to C2
configured browser of C1 to use tunneled socks5 proxy
But C2 requires proxy with authentication to connect internet.
I have set network-proxy under gnome-control-center of C2 but still i cant connect to internet from C1.
 
Suggestions welcomed.:KS

---

### Post by Lars Noodén on 2012-04-21
The proxy on C2 probably listens on a specific port.  So rather than make a dynamic (SOCKS) proxy, just forward a local port on C1 to the proxy's port on C2.


```

ssh -L 3129:localhost:3128 *c2.example.org*

```

Using that, by connecting to 3129 on the local host you are really connecting to 3128 on host C2.

---

