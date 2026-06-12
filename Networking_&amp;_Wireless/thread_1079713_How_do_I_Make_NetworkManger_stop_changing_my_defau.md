---
title: "How do I Make NetworkManger stop changing my default route?"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by CrucifiedEgo on 2009-02-24
So, this is a bit frustrating.  Here's my setup.  I have two laptops that I use in my home office.  My Ubuntu 8.1 laptop, and my work Windows XP machine.  Each of these connect to the internet(WAN) over wifi.  I have them linked together via a crossover cable so I can use synergy with no lag.  However, whenever I plug in the network cable, networkmanager sees it and changes my default route to use the gateway recieved via dhcp from the XP box.  I'd like for it to get the DHCP address (or, i can setup a static address, i don't care), and leave the default WAN route to wlan0.  Is this possible?  I'm sure it is, and I"m sure i'm making it more complicated than it needs to be, but I can't get it to work.  Every time i plug in I have to do a route add default gw/route del default gw.  Any ideas?

---

### Post by ddrichardson on 2009-02-25
[This chap]("http://kutuma.blogspot.com/2007/11/changing-default-gateway-using-network.html") seems to have it working.

---

