---
title: "Force wired PEAP RADIUS authentication"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by whitewash on 2009-11-01
Hello,
In our organization, we have an Ubuntu server, which acts (among other things) as a router (has two interfaces, eth0 goes into DSL modem, eth1 goes into switch for internal network).
So far, we've been using only primitive "security" of controlling network access, based on DHCP, known MAC address list and deny unknown-clients policy. We all know that this is very far from sufficient :) So I want to try something else.

I have looked up some articles on installing and configuring a RADIUS server, which would handle the authentication. The server is also running a SQUID proxy server, which is capable of doing radius authentication, however, what I would like, as the most optimal solution, is forcing a PEAP authentication, based on that RADIUS server (the ubuntu server would reject everything on eth1, which is not previously authenticated)
Is this possible? If so, how? (I already have freeRADIUS installed)

THX in advance :)

---

