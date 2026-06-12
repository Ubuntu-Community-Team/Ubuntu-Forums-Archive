---
title: "Something weird with open router ports and Apache 2"
date: 2013-06-20
forum: Networking &amp; Wireless
---

### Post by Notskal on 2013-06-20
Okay here's the deal.

I've been unable to open any ports on my router. Nevertheless after installing Apache2, a web server, here are the results:
[B]
Port 80 with Apache installed
[/B]
[IMG]http://i9.aijaa.com/b/00405/12363243.jpg[/IMG]

**Port 80 with out Apache**
[IMG]http://i10.aijaa.com/b/00997/12363244.jpg[/IMG]

In my router the 80 is open, but the result is different with or with out Apache. What can cause this? I hope someone got the answer 'cause that would solve my problems with the router ports :D

Thanks.

---

### Post by Grenage on 2013-06-20
Upnp ;)

Also, if the router is forwarding port 80, but nothing is listening on the PC (no Apache), then it's not really open.

---

### Post by Notskal on 2013-06-20
> **Grenage said:**
> Upnp ;)

Also, if the router is forwarding port 80, but nothing is listening on the PC (no Apache), then it's not really open.

Aha, so that's why the other ports aren't really forwarded. How can I fix this so that also the PC listens to the ports?

---

### Post by eGelor on 2013-06-20
if you want apache2 installed check your configuration file localhost and port 80-81,
then go to you router and port forward your port 80 or 81.
check if apache run ok  by rebooting it
#**sudo service apache restart**    //or something
then check your browser  localhost:80 or localhost:81
check your www/ folder for your index.html
and if you want your site in the net use a dns server if you have a dynamic ip that change every 2 hours.
some routers are closed by providers so make a call to them and ask them why the keep you so closed  for  secure or cause they don't want you to become clever? Dunno!

---

