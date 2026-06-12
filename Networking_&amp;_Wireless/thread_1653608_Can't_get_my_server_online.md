---
title: "Can't get my server online"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by parker.sikand on 2010-12-27
Hi all,

I'm trying to get my simple home web server on the internet but I cannot seem to make it work. I've set up a LAMP stack to host my website and it works perfectly on my local network (accessing from [http://localhost](http://localhost) or from [http://192.168.1.127](http://192.168.1.127)), but not from the internet. To test it for now before I set up a dynamic dns service, I am trying to access my website via my WAN IP address from within and outside of my home network (ie [http://69.**.**.**/](http://69.**.**.**/)). When I do this, I get a "taking too long to respond" message, instead of a host not found or 404 or something of that nature. My box has a pentium 4, 2 gigs of ram, and is on a DSL line so I have a hard time believing anything is "taking too long".

Here are the software packages I've installed:
-ssh
-apache2
-php5
-mysql
-phpmyadmin
-proftpd
-mediatomb

All of these packages work perfectly fine from within my home LAN, but NONE work outside of my network.

Other configs:
-My router forwards traffic on port 80 to my server
-My iptables allow incoming traffic on port 80
-My ISP, AT&T, does not block port 80 (or any port, according to various online sources)


Perhaps Apache is not configured correctly? What apache config options would be related to this problem?

I've previously tried a similar setup with the dyndns service fully configured (I followed a very thorough guide down to the t - wish I had the link it was excellent), but to no avail - I got the same "too long to respond" accessing from my domain name.

I understand that there are a multitude of causes for this problem, so what can I do to narrow down the source?

Please don't tell me to read a "How to set up a LAMP server" guide, because all of them have lead me to where I am now.

---

