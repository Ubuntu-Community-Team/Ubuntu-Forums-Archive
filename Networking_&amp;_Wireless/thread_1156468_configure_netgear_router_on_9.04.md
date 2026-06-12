---
title: "configure netgear router on 9.04"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by dbclinton on 2009-05-11
Hi,
I'm sure this isn't the first time this question has been asked here, but I haven't found the answer I need...
I'm trying to configure a Netgear WGT624v3 wireless router and I can't get any sign of life from Ubuntu. The lights on the router itself indicate that it has contact with both the internet and my laptop, but running iwconfig returns "lo no wireless extensions" etc. Internet service isn't getting through the router (it works fine when connected directly to the DSL modem as I am now) and I can't get anything via [http://www.routerlogin.net](http://www.routerlogin.net). I'm careful to always reset both the modem and the router before use...
By the way, I have no trouble logging on to other wireless networks using my Linksys card.
Thanks!
David

---

### Post by m_2009 on 2009-05-11
Do you have DHCP enabled on the router...

And id your ubuntu machine set as a static IP address or set to automatically get ip from DHCP??

---

### Post by dbclinton on 2009-05-11
> **m_2009 said:**
> Do you have DHCP enabled on the router...

And id your ubuntu machine set as a static IP address or set to automatically get ip from DHCP??
> Do you have DHCP enabled on the router...

I can't get into the router to find out.

> ...or set to automatically get ip from DHCP??

I think it's DHCP...I'll have to check.
Thanks,

---

### Post by m_2009 on 2009-05-11
Have you tried to connect to the router using a wired connection instead of wireless?

IF DHCP has somehow switched off, then most netgear routers usually use a 192.168.0.x range, so statically assign your machine an ip within the range of 192.168.0.2 192.168.0.254, something such as 192.168.0.100 should be sufficient to make sure your IP doesnt conflict with anything else that may be connected.

If DHCP has been siabled then DNS will also not be functioning therefore logging into the router using [www.routerlogin.com]("http://www.routerlogin.com") wont work as there is no DNS to resolve the hostname to an IP address.

Try typing [http://192.168.0.1](http://192.168.0.1) or 192.168.0.1:80 into your address bad in your web browser to connect directly to the routers IP address.

---

### Post by dbclinton on 2009-05-11
> **m_2009 said:**
> Have you tried to connect to the router using a wired connection instead of wireless?

IF DHCP has somehow switched off, then most netgear routers usually use a 192.168.0.x range, so statically assign your machine an ip within the range of 192.168.0.2 192.168.0.254, something such as 192.168.0.100 should be sufficient to make sure your IP doesnt conflict with anything else that may be connected.

If DHCP has been siabled then DNS will also not be functioning therefore logging into the router using [www.routerlogin.com]("http://www.routerlogin.com") wont work as there is no DNS to resolve the hostname to an IP address.

Try typing [http://192.168.0.1](http://192.168.0.1) or 192.168.0.1:80 into your address bad in your web browser to connect directly to the routers IP address.
> Have you tried to connect to the router using a wired connection instead of wireless?

No, though it's the kind of mistake I might have made, I knew enough this time to avoid it.

> so statically assign your machine an ip within the range of 192.168.0.2 192.168.0.254

Do I do that in etc/network/interfaces?
Oddly enough, my interfaces file contains less than I expected:
=====================
auto lo
iface lo inet loopback

[the following looks for a DSL connection at boot]
auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up #line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth inet manual
====================

> Try typing [http://192.168.0.1](http://192.168.0.1) or 192.168.0.1:80 into your addres

That didn't work either (I also pushed the "reset factory settings button" on the router).
I really appreciate your help!

---

### Post by dbclinton on 2009-05-23
Just in case anyone else runs into this problem, I figured out a really simple work-around:
I put Ubuntu 9.04 into the CD drive, booted and ran a live CD session. Had no trouble at all logging into the router!

---

