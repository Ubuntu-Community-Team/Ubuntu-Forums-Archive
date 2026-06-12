---
title: "Configuring proxy with one net interface"
date: 2012-05-10
forum: Networking &amp; Wireless
---

### Post by absoord on 2012-05-10
Hi all!

I'll do my best trying to explain what I want to do :-)

I want to install a web cache proxy server on my local net, so any web traffic from a desktop in the local net has to go trough that proxy.

I've chosen Squid, the configuration is ok, works fine... Now the question is:

How can I make ANY desktop connected to the network redirect its web traffic to the proxy server? I've seen many manuals having a proxy server with 2 net interfaces (eth0, public; and eth1, private), having this schema: [http://www.tutoriales-ubuntu.com/wp-content/uploads/2009/04/proxy-squid.jpg](http://www.tutoriales-ubuntu.com/wp-content/uploads/2009/04/proxy-squid.jpg)

But in my case, the proxy server is also behind the switch, and the switch directly connected to the router; so my proxy server has only one net interface (eth0).

Could someone tell me how can I configure this?

Thanks so much!

---

### Post by juliohm on 2012-05-10
Seems to me like you want to play around with "iptables". Sorry for not giving details, I'm not an expert on it.

But there must be a ton of tutorials on how to turn an ubuntu machine into the network's main router.. It is possible redirect your local network traffic through that machine and do whatever you want with it.

My guess is this is just a matter of mastering iptables.

---

### Post by absoord on 2012-05-11
Ok, iptables was one of the solutions, but I finally set the interfaces manually on the desktop comps, setting the default gateway to the server proxy. Now it works! :-)

Thanx for the idea, I'll download a few iptables to learn a lil' bit more.

---

