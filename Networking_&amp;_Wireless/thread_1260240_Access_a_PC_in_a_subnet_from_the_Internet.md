---
title: "Access a PC in a subnet from the Internet"
date: 2009-09-07
forum: Networking &amp; Wireless
---

### Post by tushar_t on 2009-09-07
So supposing I have a LAN with 2 PCs with subnet IPs of 192.168.2.2 and .3 (router being .1) and I'd like to connect to one of them for file sharing using sftp from anywhere on the public Web. Now a static IP is really useful in this case I understand, but lets just say I know the public IP address of my LAN at any given point.

How can I access 192.168.2.3, for instance, from outside if I know my public IP?  This is assuming all computers use Ubuntu.

---

### Post by jward3010 on 2009-09-07
You'll have to go to your router configuration page and open necessary ports for SFTP and direct them towards the 192.168.2.3 machine. It's pretty easy to do. The port number for SFTP is 22.

Also, if you have a dynamic public IP (which most home users have) then you can set up an account with DynDNS.com to match your constantly changing public IP to DNS name for example: "tushar.dyndns.org" - No matter what you're public IP address is on your router all you'll ever have to type is "tushar.dyndns.org" and it will resolve correctly. Hence connecting to an FTP server on your network will look like this "ftp://tushar.dyndns.org").

---

### Post by tushar_t on 2009-09-07
Thanks. That was surprisingly straightforward! :)

---

### Post by tushar_t on 2009-09-08
Another quick question: suppose I want the second PC within the subnet to be accessible via SSH from outside the LAN. Do i then configure another port to be forwarded to the 2nd PC and force SSH client and server (on the 2nd PC) to use that port instead of 22?

---

### Post by jamest09 on 2009-09-08
Yes that's right, google for NAT and PAT

---

### Post by jward3010 on 2009-09-08
> **tushar_t said:**
> Thanks. That was surprisingly straightforward! :)

Depending on your router config page, it may very well be straightforward, or maybe not. Some are horrible messes.

> **tushar_t said:**
> suppose I want the second PC within the subnet to be accessible via SSH from outside the LAN. Do i then configure another port to be forwarded to the 2nd PC and force SSH client and server (on the 2nd PC) to use that port instead of 22?

I'm not completely sure about SSH access and whether the ports are interchangeable, I've dealt with it only on a LAN - in most cases they are, you usually just have to configure putty (or whatever you use) to use a different port for SSH, probably has a custom option. Or of course configure SFTP during setup to use port 23 for example

---

### Post by tushar_t on 2009-09-08
Great. Thanks again guys.

> **jward3010 said:**
> Depending on your router config page, it may very well be straightforward, or maybe not. Some are horrible messes.
I have a slightly unusual setup:

Phone cable --> (modem+router)--> wireless router --> PCs

But just by extending your logic and a bit of guesswork, I forwarded port 22 from the modem to the wireless router and then did the same again from the wireless router to my PC. Works perfectly!

Also installed ddclient after registering with DynDNS.com, so it's all good.

---

### Post by jward3010 on 2009-09-09
> **tushar_t said:**
> Great. Thanks again guys.


I have a slightly unusual setup:

Phone cable --> (modem+router)--> wireless router --> PCs

But just by extending your logic and a bit of guesswork, I forwarded port 22 from the modem to the wireless router and then did the same again from the wireless router to my PC. Works perfectly!

Also installed ddclient after registering with DynDNS.com, so it's all good.
Yay!

---

