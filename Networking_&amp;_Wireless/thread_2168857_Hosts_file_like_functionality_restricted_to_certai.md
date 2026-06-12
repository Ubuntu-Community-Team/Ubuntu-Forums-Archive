---
title: "Hosts file like functionality restricted to certain WIFI network"
date: 2013-08-19
forum: Networking &amp; Wireless
---

### Post by Kasuko on 2013-08-19
I have a really weird router that is forced on me by my ISP. It has an incredibly odd bug where if I am behind the router and I try to access something within my local network through a public IP then it goes to my routers remote admin page.

Let me explain with an example.

I have my laptop (192.168.0.2) and a server (192.168.0.100), I also have a static IP (12.34.56.78) for my router. On my server I have a simple web host set up on port 80. If I am on my home network visiting 192.168.0.100 in a browser I get the desired web page, if I am NOT on the home network and I connect to 12.34.56.78 I get the desired web page. However if I am on the home network and I attempt to visit 12.34.56.78 I get my routers remote admin page. Now this is a confirmed bug with the router and the only way I would be able to fix it is by some how convincing my incumbent ISP provider to release new firmware for the router ... aka not going to happen.

This makes configuring things on my laptop very difficult because I have to decide which IP to use depending on where I am. I was wondering if there was a way I could set up a host like file but only when I am connected to my home WIFI network to redirect all calls to 12.34.56.78 to 192.168.0.100?

Thanks
Kasuko

---

### Post by steeldriver on 2013-08-19
The feature you are looking for is usually referred to as 'NAT loopback' I think - many consumer grade routers don't support it out of the box (although some can be reflashed with tomato / dd-wrt / whatever to do so)

[http://en.wikipedia.org/wiki/Network_address_translation#NAT_loopback](http://en.wikipedia.org/wiki/Network_address_translation#NAT_loopback)

---

### Post by Kasuko on 2013-08-19
> **steeldriver said:**
> many consumer grade routers don't support it out of the box (although some can be reflashed with tomato / dd-wrt / whatever to do so)

Again, I do not have control over the router. If I don't use the router they gave me with their firmware I don't get TV. Using a different router or firmware is out of scope of solving this issue.

I just want to set up the "NAT loopback" only on one laptop.

---

