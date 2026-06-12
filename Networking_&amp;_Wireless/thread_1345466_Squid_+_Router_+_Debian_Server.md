---
title: "Squid + Router + Debian Server"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by Lamez on 2009-12-04
Okay, I am trying to setup a Proxy server that has a web frontend and forces users to login to use the internet. 

I am having trouble getting squid to work for me.

Here is my old setup:

Modem => Router => Clients

Here is what I THINK I need:

Modem => Proxy Server => Router => Clients

Right? Not sure.

Also do I need to disable the DNS server within the router?
My Squid server also is a Samba server, can I access the Samba server while running a squid server? In all, how can I setup a proxy server behind a router with a web frontend forcing users to login with a correct password?

Thanks, I have done tons of googling searching, let me know if anyone has anything!

-James Little :P

---

### Post by Lamez on 2009-12-04
anyone? anything? anyplace where I can request info, like another fourm?

---

### Post by Nostalos on 2009-12-04
> Modem => Proxy Server => Router => Clients

Don't think this is what you are looking for.  If you did this, you might as well remove the router and make the proxy server the router/firewall for your clients.

Proxy Server should be sitting on a seperate network off of the router. or technically can be sitting on the same network as clients.  Also you are wanting to do proxy authentication so Transparent Proxy is out of the question.   So you will need to.

1.  Set up Router to NOT accept outbound traffic from anything BUT the proxy server.

2.  Manually configure every browser on the network to point to that proxy specifically OR use some type of proxy autoconfig set up.


You CAN do transparent proxy with some firewall redirects and trickery, but you lose the ability to do authentication at this point.


Here is a little info on Proxy auto discovery [http://en.wikipedia.org/wiki/Web_Proxy_Autodiscovery_Protocol](http://en.wikipedia.org/wiki/Web_Proxy_Autodiscovery_Protocol).   But I recommend not using it as it is not without its security concerns.

---

### Post by Lamez on 2009-12-05
No, I do want a transparent proxy. That does not throw out any authentication. There is a built in "plug-in", if that is the proper name, that allows one to setup a password and requires the user to enter the password before browsing the net. I looked this up after posting this. I am also not going through the hassle of configuring everyone's browser's. I also have a lot of laptops on the network that venture out, then when they come back I would have to reconfigure them. (So that's a definite no.)

However, I am still having troubles getting the proxy transparent. The proxy is also denying all connections, or refusing if you will. After getting the hardware settings right, which is:

Modem => Router => Proxy + Clients. (I really don't think that is right, but whatever).

How do I force everyone on the proxy without configuring everyone? My routers are running DD-WRT, so that might help out.

Any ideas?

---

### Post by Nostalos on 2009-12-06
> **Lamez said:**
> 
Modem => Router => Proxy + Clients. (I really don't think that is right, but whatever).
Any ideas?

You would only need your proxy inline if it was actually managing the flow of your traffic and doing the redirect itself.  And yes I am aware proxies do authentication.  However I do beleive in transparent mode, proxies are no longer able to.  However that may just be a limitation of the ones I use for the 50K employees I support.

[http://www.dd-wrt.com/wiki/index.php/Squid_Transparent_Proxy](http://www.dd-wrt.com/wiki/index.php/Squid_Transparent_Proxy)

---

