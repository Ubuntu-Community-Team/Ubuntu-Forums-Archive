---
title: "Routing 192 and 10 by eth0, all other addresses through ppp0"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by obirenokenobi on 2009-07-27
Hi! I'm in an enterprise network with very restricted Internet access, so I bought a CDU card from my cell provider in order to have unrestricted Internet access.

My problem with this, is that I'm not able to surf the Web and surf the local network. I have to shut down the modem in order to have full access to my local network, of course, by doing this, I'm barred from the Internet.

So what I want is to "route" all IPs of 192.x.x.x and all of 10.x.x.x through my wired card (eth0) and anything else, through the modem (ppp0)

I've tried to do it with route command, but everything is always routed through eth0 unless I remove the gateway information. But... if I remove the gw for the eth0, many ips in my local network can't be accessed. So I need to have a full configured eth0.

What can I do? Which commands can I use?

Thanks!

---

### Post by obirenokenobi on 2009-07-27
I'm very sorry for this post. I tried the following and worked:

Remove the gateway (put instead 0.0.0.0) from eth0

Execute the route command but now telling it to use certain gw:
route add -net 10.4.160.0 netmask 255.255.255.0 gw 10.2.123.254 dev eth0

Restarted network.

Voilá!

Now I can access those addresses through eth0 and all other traffic is routed by ppp0.

This worked well, but I'm open to read other, more efficient and easy, approaches.

Many thanks!

---

