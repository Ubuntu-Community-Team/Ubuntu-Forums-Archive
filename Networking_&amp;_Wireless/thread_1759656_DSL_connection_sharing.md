---
title: "DSL connection sharing"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by greg@pottsfamily on 2011-05-16
My internet provider delivers my signal via PPoE.  I currently access this through a router, and have the router configured to pass applicable incoming traffic to the linux box.

BUT... When I am working inside the router I can't access ftp or http services on my linux box correctly, as the DNS server points to the router, which is in fact an http server as well. This makes site editing a big PITA, as you might imagine.

I would like to position my linux box upstream of my wireless router, and then  share the signal to the router for distribution to the rest of my users.

But for some reason it seems that DSL connections can't be shared. I tried using firestarter and it can't do it either. What's so special about PPoE that it can't be shared in linux? Mac's and PC's can do this right out of the box; it's kinda depressing if my linux machine can't do likewise. (I don't actually trust a PC outside the wire and I don't own a mac stable enough, or I might actually have used one)

Recommendations would be appreciated.

---

