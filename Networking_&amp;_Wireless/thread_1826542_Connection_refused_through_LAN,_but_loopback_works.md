---
title: "Connection refused through LAN, but loopback works?"
date: 2011-08-16
forum: Networking &amp; Wireless
---

### Post by evencoil on 2011-08-16
This problem started happening after I changed routers from a 2WIRE to a Medialink.

I want to ssh to my desktop, standard port 22.

The desktop is set to update a dyndns domain name.

The router forwards port 22 to the desktop.

If I ssh to the domain name from another computer on the network, then I can connect to the desktop fine.

If I try to ssh to the desktop's internal IP (i.e. within the router), then I get "connection refused."

The same thing happens for other services besides ssh.

Also, I can ssh internally to other computers on the network, so it appears to be something with the desktop's network settings.

Can anyone see what's going on here?

---

