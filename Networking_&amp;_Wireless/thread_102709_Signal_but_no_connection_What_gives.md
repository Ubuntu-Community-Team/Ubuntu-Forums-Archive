---
title: "Signal but no connection? What gives?"
date: 2005-12-12
forum: Networking &amp; Wireless
---

### Post by TX7 on 2005-12-12
I've put my Linksys  WPC11 into my Dell Dimension 3700 laptop, and everything has worked so far, but I haven't gotten a connection yet. It has detected the card, created Eth1 for it, labeled as a wireless connection. I'm using DHCP with 192.168.15.1 for DNS server, and when I gave it my WEP key and network name, it shows me the signal strength, varying with how close I am to the router. 

However, when I go into FireFox and attempt to go to a website, it gives me the error "www.google.com cannot be found. Please check the name and try again". 

I have disabled my eth0 connection,  and set my primary gateway to eth1. What else do i need to do to get it to work?

Sorry. I'm a newbie =D

---

### Post by jafenske on 2005-12-12
Did you try setting a static IP...

---

### Post by TX7 on 2005-12-12
Trying that now.

---

### Post by TX7 on 2005-12-12
Yes! It works! I accidentally put in the wrong WEP key, apparently.

---

