---
title: "Restricting Network Access (Web) to only Certain IP Addresses"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by kyleflan on 2009-02-04
My school is hosting a programming contest and I'm in charge of developing the network. The biggest challenge is restricting web access to only a few sites and a network printer. (i.e. allow access to the Java API and an online checker only)

The network computers will be connected to a switch that connects to a router that connects to the internet.

What would be the best way to accomplish this?

TIA,
Kyle

---

### Post by pdtpatrick on 2009-02-04
create a proxy server and block all web access except the allowed site.

---

### Post by sedawk on 2009-02-04
Are you allowed to reconfigure that router? Are other people needing
that router to connect to the internet? Will you be in big trouble
if you mess up the internet connection for other people?


Let's assume you are not allowed to touch that router.
Then there are two ways. A more secure way with some
extra hardware and a more insecure way without extra hardwae.

With extra hardware:
Connect all "contest" PCs to a "contest" switch that is not
connected to anything else.
(So "contest" PCs use some private IP network like 10.1.1.x)
Add a another machine to that network that has two network cards,
one is connected to the "contest" switch and the second one
to the normal network, so you can get into the internet.
On this machine you can install a proxy (e.g. squid or privoxy) that has
a whitelist of allowed web servers.

The only way from your "contest" PCs to the internet is via your
proxy PC. 

Without extra hardware:
Configure your private network as above. The proxy only has one
network card, but two IPs for that card, one for the private net
and the normal one (to connect to the internet).
Configure the "contest" PCs so the do not know how to connect to
the internet (e.g. static IPs, not default route to the internet router).
This should work, but there is a small risk that people (if they 
have admin or root access) can alter the network configuration and
get direct access.

---

### Post by kyleflan on 2009-02-09
Thanks for the replies. I can configure the router however I'd like, so are there any universal ways to set up a whitelist on routers? I understand that routers are different, but if anyone could point me to a decent tutorial or resource, I'd appreciate it!

Thanks again,
Kyle

---

