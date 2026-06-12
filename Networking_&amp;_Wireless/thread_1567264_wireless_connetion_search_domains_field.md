---
title: "wireless connetion search domains field"
date: 2010-09-03
forum: Networking &amp; Wireless
---

### Post by allsport on 2010-09-03
Hello,
 
Very new to this. Please help if you can.
 
I have installed ubuntu netbook addition and all is good, but when I try to connect to internet I get comcast(my service provider) site. Which means I am connecting to outside world just need to know what to enter in Search Domains field.
 
All my pc's/laptops at home have 2 DNS names entered for ipvr4 listed in the field but no Search Domains field value specified and it works great off of wireless router.
 
Well here when I go to IPvr4 tab it seems like I am required to enter value in search domains field. The question is what do I enter there COMCAST domain? Like this one: [FONT=Verdana][[COLOR=#800080]hsd1.il.comcast.net[/COLOR]]("http://www.dslreports.com/archive/comcast.net")?[/FONT]

[FONT=Verdana]Thanks for all your help[/FONT]

---

### Post by MaindotC on 2010-09-03
You don't have to enter anything.  Comcast sends you DHCP information which will be listed in /etc/resolv.conf amongst other places.  Just leave it as is.

---

### Post by allsport on 2010-09-03
thanks for the reply,
 
thing is on my other laptop (windows) if i left it blank (automatic) I get to comcast page. if I switch to manual and enter dns names it works!
 
So I wanted to do the same thing here by changing my connection (my home network settings) same way as I do on windows. but here it seems like it requires search domains field otherwise apply button is disabled.
 
Don't know what to enter there. Can I enter same value as in DNS names field?
 
Any thoughts?

---

### Post by MaindotC on 2010-09-03
You shouldn't have to enter anything!  Comcast will send you the information you need via a protocol called DHCP.  I'm probably misunderstanding what's going on here but you shouldn't need to enter anything.  Can you take a screenshot of this "search domains" field you speak of?

---

### Post by allsport on 2010-09-03
Attached is the screen shot from windows where I need to specify DNS names in order for the Internet to work. here you only have 2 fields to fill out, but in Ubuntu if you go to ipv4 tab in wireless settings it has another field Search Domains. I'll get the screen shot when I get to my laptop in an hour or so 
 
Thanks for all your help.

---

### Post by MaindotC on 2010-09-04
In windows you should be choosing "obtain DNS server addresses automatically".  In Ubuntu, choose Method: Automatic (DHCP).  You really should have no reason for editing these settings and please leave them all to automatic.

---

