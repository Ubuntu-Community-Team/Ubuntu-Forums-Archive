---
title: "Can I use a cheap cable or do I have to buy expensive gear"
date: 2013-02-15
forum: Networking &amp; Wireless
---

### Post by CaptainMark on 2013-02-15
I know very little about networking so I'll try to explain what I want to do in basic terms. Picture this:
I have an internet router plugged in my front room
I have a 10m ethernet cable I spent a lot of effort some years ago putting through the walls myself leading to my lounge
In the lounge I currently have a raspberry pi attached to this 10 ethernet cable
I have a xbmc media server next to the raspberry pi that I also want to network into my home lan

Now laying another 10m cable is not practical as it involved lots of effort, 20 inch long drill bits and me breaking a sweat (which I loathe to do)

My question is can I use a cheap ethernet splitter (single male to double female) and two short ethernet cables to do this  or am I going to need a special hub or switch. Failing this can I use another cheap easily available adapter to get this to work without expensive extras

My linux knowledge is fine but please remember my experience with networking is minimal. 

Ps, I've attached a pic of what I mean, I don't know if this will work, and sorry, wifi is not an option here, as they are both super low power units that do not carry enough current to power a wifi adapter

---

### Post by oldfred on 2013-02-15
Years ago I had (still have somewhere) a 4 port hub. That is a splitter. Back then switches were expensive. 
But now switches hardly cost more than hubs, so I would suggest a switch (unmanaged). Managed offer many more business type features but are more expensive.

I am not sure what is good. Quick Google search found this netgear.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833122005](http://www.newegg.com/Product/Product.aspx?Item=N82E16833122005)

others when looking for hub gave switches?
[http://www.newegg.com/Product/ProductList.aspx?Description=4%20port%20ethernet%20hub&Submit=ENE]("http://www.newegg.com/Product/ProductList.aspx?Description=4%20port%20ethernet%20hub&Submit=ENE")

---

### Post by Sef on 2013-02-16
An inexpensive switch would be best. Will work much better than a hub.

---

### Post by kurt18947 on 2013-02-16
You wouldn't have access to an old router, would you?  If so, you can disable routing, firewall and wireless if installed and use it as a switch.  I did this with a second router but am using it as a wireless access point as well.  Most have 4 ethernet ports.

---

### Post by CaptainMark on 2013-02-16
I do have an old router laying around, I'll look into that option thanks

---

### Post by kurt18947 on 2013-02-17
> **CaptainMark said:**
> I do have an old router laying around, I'll look into that option thanks

If you go that route, you'll want to make sure the I.P. address of the secondary router is different than the primary.  For instance, primary is 192.168.1.1,  make your secondary 192.168.1.2, same subnet.  I turned off the firewall and DHCP server functions on the secondary router.  Run the cable from the primary router to one of the LAN ports, not the WAN port.  It should work.  If there's a version for your secondary router and you want to teach an old dog new tricks, you could look into DD-WRT or similar.

---

