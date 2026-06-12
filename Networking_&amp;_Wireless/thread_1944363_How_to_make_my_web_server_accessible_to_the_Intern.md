---
title: "How to make my web server accessible to the Internet?"
date: 2012-03-21
forum: Networking &amp; Wireless
---

### Post by armukul on 2012-03-21
I have configure apache2, php-5, and mysql server on 10.04 LTS ubuntu.. my web server is working well in local LAN.. now how can i make this web server accessible to Internet???

Thanks....

---

### Post by SlugSlug on 2012-03-21
forward port 80 (and/or 443 if https) from your router to your webserver 


connect via external IP address

---

### Post by alarme on 2012-03-21
You must configure your router to NAT port 80 to server lan IP
and configure properly the router firewall to allow incoming connections to this IP
Google for "router open ports"

---

### Post by aura7 on 2012-03-21
@SlugSlug Can you please tell how to forward port 80 from the router...

---

### Post by SlugSlug on 2012-03-21
portforward.com

---

### Post by gordintoronto on 2012-03-21
It's also possible that your ISP will block the connection. Many residential Internet providers have "Terms of Service" which prohibit running a server.

---

