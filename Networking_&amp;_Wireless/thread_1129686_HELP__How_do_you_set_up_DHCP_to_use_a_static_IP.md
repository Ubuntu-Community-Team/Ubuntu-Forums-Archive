---
title: "HELP:  How do you set up DHCP to use a static IP?"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by theosib on 2009-04-18
Ubuntu seems to default to DHCP.  And I find plenty of how-tos that explain how to configure static IP manually.  

But what I would like to know is how to it up to use DHCP with a fixed IP address.  I've done it before with Gentoo (but I don't remember how).  The advantage here is that all of the other network settings (masks, DNS, etc.) are automatic, while only the IP address is fixed, and I want to do this because I'm setting up a server.  Also, whenever I've done static IP address before, I have DNS problems.

Any ideas?

Thanks!

---

### Post by lisati on 2009-04-18
I set my router to use static IPs for all the machines I'm likely to connect to it. That way, I could use Ubuntu's default of DHCP and still know which machine is where.

---

### Post by theosib on 2009-04-18
Well, I'm not sure if I can set my router to do that.  Maybe.  But why should I have to do that?  And how do I setup Ubuntu do be in control of this?

Thanks.

---

### Post by Iowan on 2009-04-19
> **theosib said:**
> But why should I have to do that? DHCP address is controlled by DHCP server, *probably* your router. On my network, I turned off the DHCP server on the modem, and use another machine as DHCP server. I haven't tried it yet, but Dnsmasq (available in repo's) > ... is a lightweight, easy to configure, DNS forwarder and DHCP server.

---

### Post by Copernicus1234 on 2009-04-19
Not sure if this is what you want, but I have setup my machines so that they use DHCP to get a ip address from the router, but they get the same ip address every time since I have allocated specific ip's for specific client mac addresses in the router.

So every machine gets the same ip every time from the dhcp server. Solves all kind of problems with port forwarding going to the wrong machine etc.

Also gives the advantage that every machine, weather its Linux, Windows or Mac, doesnt have to be configured in any specific way. All configs are done in the router.

---

