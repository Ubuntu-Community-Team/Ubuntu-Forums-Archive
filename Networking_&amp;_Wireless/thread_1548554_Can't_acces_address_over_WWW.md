---
title: "Can't acces address over WWW"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by ductiletoaster on 2010-08-08
I am Setting up a DVR for a web security system and I have run into some problems accessing it over the internet. The provides us with an address so it can be accessed over the internet. However the only way i can get to the web interface is via the local ip address.

1) I forwarded the appropriate ports and used an online tool to verify they were open.
2) I can access it using the local ip but not the provided address.
3) if i ping the address with http:// in front there is now response however if i remove the http:// and ping the address i get a response.

Any Suggestions?

---

### Post by Iowan on 2010-08-08
From where are you trying to access the system? Some routers won't "port-forward" an internal address back to an internal address. 
I also can't ping my modem/router if I try it with http://<router address>, although I can ping it without http:// and can connect via browser and http://<router address>.

---

### Post by ductiletoaster on 2010-08-25
Sorry for the late reply but i realized the same thing that you mentioned. I can ping the dvr using an internal address from a computer with in the network but not using an external address.

SO i decided to go home and try accessing the dvr from my computer and BAM it worked perfectly using the external address.

---

