---
title: "Ubuntu 10.10 switched from network manager to WICD and now all DNS resolution fails"
date: 2012-03-04
forum: Networking &amp; Wireless
---

### Post by shadowwolf225 on 2012-03-04
Trying to post again....last time the post failed after a page long description

Network manager was getting on my nerves with either constantly connecting to a network or asking me to do so.  I dont want to have to disable my wireless (i use 2 adapters) just to get it to shut up.  So I decided to use WICD.  I installed WICD and then later removed NM. Now i can connect wired or wireless and ping any valid ip (including the google dns servers I use) but no matter what dns I try to use with wicd or even letting dhcp auto configure it, I cannot get the machine to resolve hostnames.  nslookup fails with a connection timout. I can't reinstall NM because without DNS the interwebs are effectively broken  Any help is appreciated

---

### Post by shadowwolf225 on 2012-03-04
Fixed
sudo nano /etc/resolve.conf 

#added 

nameserver 8.8.8.8
nameserver 8.8.4.4

Ctrl+O
confirm write
Go back into WICD disconnect....connect
Working :D

---

