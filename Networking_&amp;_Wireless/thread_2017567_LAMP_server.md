---
title: "LAMP server"
date: 2012-07-05
forum: Networking &amp; Wireless
---

### Post by simoninman on 2012-07-05
Good evening, i have an ubuntu box at home running a lamp server, i have tried to redirect one of my online subdomains to that server however my ip address is the same on all of my computers at home and it does not seem to be pointing to the ubuntu server correctly?
does anybody know how i can fix this?

---

### Post by alexlpratt on 2012-07-05
This really depends on how your router is setup in conjunction with your Ubuntu box. You may want to utilize port forwarding for this: [Port Forwarding Wikipedia]("http://en.wikipedia.org/wiki/Port_forwarding"). Good Luck!

---

### Post by SeijiSensei on 2012-07-05
If you're getting the default "It Works!" page rather than the domain you expect, you need to check the virtual host definition.  Apache selects the virtual host based on the server name specified in the URL.  It matches that against the "ServerName" directive in the <VirtualHost> container.  For details, see [http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html).

---

