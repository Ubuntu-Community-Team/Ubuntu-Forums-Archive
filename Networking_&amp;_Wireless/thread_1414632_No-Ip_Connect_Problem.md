---
title: "No-Ip Connect Problem"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by wisie on 2010-02-23
I've recently installed noip2 which installed fine. Except when I try connect to my noip domain it sends me to my router login page and won't let me access my ubuntu box.

How can I set my noip domain so when I connect, it will allow me to access SSH, sabnzbd, etc instead of forwarding me to the router login page.

I'm sensing that I may have to set the ubuntu box to a static ip and forward the various ports of SSH, sabnzbd, etc to it. Would this be correct?

Thanks

- Alex

---

### Post by nickmcg on 2010-02-24
You are correct, you will need to set your router up to forward the ports you want to your ubuntu box, and you will have to give your ubuntu box a fixed ip address unless your router can forward to a named machine.

I would also advise shutting your router's login access off from the outside world (just paranoid)

Cheers

Nick

---

### Post by Dayofswords on 2010-02-24
this may be obvious, or not

but the noip domain uses your external address, so you cant use it for lan

---

### Post by nickmcg on 2010-02-26
You're right, it's obvious once you know.

On my setup, all incoming port 80 (http) requests from 'the outside world' are routed to 192.168.0.12 on the lan, and the router always allocates that address to that machine.
On a netgear router, the fixed ip is on the 'LAN setup' page, and the port redirection on the 'Firewall rules' page.

Some routers make this easier than others!

Cheers

Nick

---

