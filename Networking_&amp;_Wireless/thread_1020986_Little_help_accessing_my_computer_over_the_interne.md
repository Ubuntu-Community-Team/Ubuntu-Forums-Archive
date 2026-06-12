---
title: "Little help accessing my computer over the internet"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by Th0rn0 on 2008-12-24
Hello all and a Very merry Christmas (or happy holidays)


I am sat here atm, scratching my head.

I have multiple servers/Computers that I want to access over the internet. I have a Netgear DG834 Router. The ports in question is on my WAMPServer on my Windows PC, my Webserver on my Freenas box and my Apache webserver on my Ubuntu box. Now they are all using port 80 as far as I know. But, I cannot access anything from my public IP on my network. It jsut times out. However I can access my router's config.

Any idea on how to set specfic external and internal ports? I've looked everywhere. I have also tired access the servers with just one turn on and changing the port. No luck...

Any thoughts?

---

### Post by Iowan on 2008-12-26
Have you set up port forwarding on the router (and do you have fixed ip address - or account on mo-ip or something similar)? I've never done port-forwarding, but it might be possible to forward , say router port 80 to WAMP port 80, router port 81 to FreeNAS port 80, router port 82 to Apache port 80, etc.

---

### Post by superprash2003 on 2008-12-26
you could use this guide for port forwarding [http://www.portforward.com/english/routers/port_forwarding/Netgear/DG834/default.htm](http://www.portforward.com/english/routers/port_forwarding/Netgear/DG834/default.htm) .. apart from that you need to tell firestarter( if present) to allow port 80

---

