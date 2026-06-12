---
title: "How do I make an ubuntu computer have a static IP?"
date: 2013-06-15
forum: Networking &amp; Wireless
---

### Post by vikkydonlad on 2013-06-15
[COLOR=#333333][FONT=arial]I want to use an ubuntu computer (desktop edition, not server edition) as a server so I can access it while I am not in the house.
___________________________
[/FONT][/COLOR][ drupal developer ](http://www.freeenergymedia.com)

---

### Post by Lars Noodén on 2013-06-15
Welcome.

Most of the ways of remote access involve using [SSH](https://help.ubuntu.com/community/SSH) either by itself or as a means to tunnel insecure protocols in a safer way.  What do you want to be able to do remotely?

If you have ADSL or something similar, you will have to forward at least one port from your external IP on your modem or router to your desktop computer.  The method varies from brand to brand and model to model.

Lastly, if you do not have a static IP from your ISP, you will have to use a work-around like [dynamic DNS](https://help.ubuntu.com/community/DynamicDNS).  Several still offer free-of-charge services for the home user.

---

### Post by ahallubuntu on 2013-06-15
~

---

### Post by houstonbofh on 2013-06-15
As stated, your first step is getting to your router.  This can be a static IP from your ISP, or some type of dynamic dns service like no-ip.org.

Once that is configured, then you have to get THROUGH your router, which usually means NAT pinholes of some type.

Next is making sure you find the server, which could mean static IP inside, or some type of dynamic NAT like you find on the 2wire devices.

---

