---
title: "Set default gateway from other subnetwork"
date: 2012-09-16
forum: Networking &amp; Wireless
---

### Post by ash_kpi on 2012-09-16
We have 10.0.0.0 private network. I connect to network via wifi and get 10.103.7.xxx ip address, 255.255.255.128 netmask and gw 10.103.7.129. The problem is that we share internet connection through gateway 10.103.6.36. I can ping this host, but I can't set 10.103.6.36 as default route. I'm getting "no such process". I tried this workaround [http://www.adminsehow.com/2011/09/gateway-on-a-different-subnet-on-linux/](http://www.adminsehow.com/2011/09/gateway-on-a-different-subnet-on-linux/) but no luck.

So I need smth like this:
10.103.7.xxx -> gw1 10.103.7.129 -> gw2 10.103.6.36 -> internet

I spent whole day trying to figure out how to configure network. Any help will be very appreciated.

---

### Post by dandnsmith on 2012-09-17
There are a couple of points I don't understand
- if you have a subnet 10.103.7.xxx, why isn't your mask 255.255.255.0?
- you can expect to get to 10.103.7.129 from 10.103.7.xxx, but how on earth can you get to 10.103.6.36, as it isn't apparently anywhere accessible: what is the connection (are they on the same machine?), and you need a physical means of connection before you can establish routes.

Further info would help

---

### Post by ash_kpi on 2012-09-17
Hey, Derek

10.103.7.xxx is not subnet. That's my wifi ip address, I just forgot it because I wrote from another computer. If I'm correct it's 10.103.7.160. So netmask must be correct 255.255.255.128.

10.103.7.129 is router that allows to get any host in 10.0.0.0/24 subnet.

10.103.6.36 is another router that has access to internet.

My initial thought was that if I can ping 10.103.6.36 than I can send packets through that router. I messed that this ping goes through 10.103.7.129 but ip package has only one address (final destination) and it gets default router by link layer of TCP/IP stack. Sorry on that.

Now I'm going setup open vpn server on 10.103.6.36 and establish tunnel connection. But that's another question.

Anyway thanks.

---

