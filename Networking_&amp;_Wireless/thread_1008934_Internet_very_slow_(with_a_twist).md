---
title: "Internet very slow (with a twist)"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by ecom on 2008-12-12
i'm experiencing very slow internet. web pages take a long time to load but here's the twist: after the web site loads, the internet becomes fast again. any ideas how this happened, guys?

i mean, if i type for example, [www.youtube.com](www.youtube.com), firefox takes a long time to load the website but after youtube loads, and i search for some vids, the internet speed quickens. weird. i already enabled cookies and stuff. and i didnt change any firefox settings.

i'm running ubuntu 8.10

help.

---

### Post by sonofusion82 on 2008-12-12
my guess is DNS name resolution is the slow part.
try to figure out the IP address of say [www.youtube.com](www.youtube.com)
perhaps due to DNS server settings?
how about when u change to OpenDNS?

---

### Post by anubhavrocks on 2008-12-12
If you directly use the IP of the site in the browser,does the site load faster?

---

### Post by superprash2003 on 2008-12-12
yes mostly DNS issue, try using opendns servers - 208.67.222.222 and 208.67.220.220 [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by ecom on 2008-12-21
how do u change DNS? 

but i dont think this is a DNS issue. i mean, if i type a website, the browser takes very long to load it but after the website appears, and i click on something, the linked page loads very quickly.

i tried firefox, opera, epiphany, same problem for all of them.

i didnt mess with any of their default settings or any ubuntu 8.10 settings. 

help.

---

