---
title: "can't ping outside domain"
date: 2012-11-19
forum: Networking &amp; Wireless
---

### Post by jwalker on 2012-11-19
Hi all

I have a debian desktop instance in a corporate network. When I give it a static ip, I cannot ping or surf any hosts outside my domain.

If I use DHCP, I do not have these issues. 

The only thing I noticed is when I use DHCP, a default gateway is populated in routes, which I can see via 'routes -n'. 

When I set my ip statically, I add this route manually with the 'route add gw xxxx' command, however it does not help. 

Name resoultion is ok too, because the ping command will resolve the ip address of the site I am trying to ping. 

What is DHCP doing that I am missing?

Thanks for your help, this one has me mystified.

---

### Post by jwalker on 2012-11-19
please ignore this, the particular ip address i was using was part of a range configured on the switch to not be allowed outside comms.

---

