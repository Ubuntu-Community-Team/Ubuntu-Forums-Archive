---
title: "Forcing the system to use ONLY one of two network cards?"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by prupert on 2009-10-12
Hi

Here is my situation. 

I run Ubuntu 8.04 LTS as my main server, serving files via samba, doing video encodes and hosting a couple of websites. 

Recently I decided to up the security and I wanted to run Apache through a separate network card, that was attached to a box running snort-inline, so it could catch and block most attack attempts on the website. 

Thus, I connected a second ethernet card to the box (eth1), gave it a static IP address 192.X.X.112 and changed my Apache2 config so it only listened on that IP address. I thus gave a static IP address to the original ethernet card (eth0) of 192.X.X.111.

However, the system sometimes uses the eth1 card and the 192.X.X.112 address and sometimes the eth0 card and the 192.X.X.111 address for various network services (like VNC, SSH and samba). Apart from editing each of the services' individual configs so they only use the eth0 (192.X.X.111) card (assuming this is possible at all - for example the Remote Desktop Viewer GUI offers no options in this area afaik), is there anyway to make the system only use one particular card unless told to do otherwise?

---

### Post by i.r.id10t on 2009-10-12
Most services will by default bind to all available interfaces. 

If you just want to prevent connections, you could use iptables (firewall) to block connections on your second card to everything but port 80.   However, if you don't want the services listening on the second card at all, you'll need to modify their configs.

---

### Post by prupert on 2009-10-12
Ahh, I thought as much. I'll have to get hunting for the configs for the default ssh server and Remote Desktop Viewer (though I am sure that is not actually what it is called!).

Cheers for the reply.

---

