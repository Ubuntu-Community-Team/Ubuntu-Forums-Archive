---
title: "How to set up a Linux subdomain"
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by DrScum on 2009-09-20
I completely removed XP from my Laptop and switched to Ubuntu 9.04. Took me about a week to have all software working all data, e-mails, bookmarks and adress books recovered to the new linux apps.

The last two items are backup routine and networking.

I have a WLAN router connected to several windows workgroup members and to a Ubuntu 8.04 desktop via Wlan connections. My laptop also connects to the router via WLAN. All of this works fine.

What I can't get to work is a Linux subdomain connecting my Laptop and another Linux machine to the Ubuntu 8.04 desktop using a ethernet connection. The ethernet cards are configured to another IP group than the wireless cards, according to the ifconfig output they are up and running and they can ping each other. However, I can't get the file sharing going. I tried Samba but couldn't get it to work.

Anybody able to help me out?

---

### Post by i.r.id10t on 2009-09-20
Assuming there are no firewall issues and other aspects of just having a network are working, then you should be able to click on "Places" in the menu bar and then pick Connect to Server and be able to connect to the windows machines either by name (if you have local name service) or by IP.  To get the windows machines to Linux, you'll need to set up samba server- lots of howtos out there...

---

