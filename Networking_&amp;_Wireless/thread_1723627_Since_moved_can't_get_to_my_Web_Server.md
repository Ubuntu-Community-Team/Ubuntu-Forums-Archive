---
title: "Since moved can't get to my Web Server"
date: 2011-04-07
forum: Networking &amp; Wireless
---

### Post by macmike on 2011-04-07
I have recently moved. I was on a comcast Internet system and had the Server working there. I have moved to where I am on a different server. I have been issued a static IP address. I have configured my Linksys server to reserve an address for my Ubuntu Web Server. When I try to get to my web site the connection times out not getting there. I remembered I had to forward some services, ports over to the reserved IP address for the server. I can't for the life of me remember the ports I forwarded. Can someone help me with how to get this forwarding done. Or what else might be keeping me from seeing my webpate - mikealrhughes.com?

Thanks

---

### Post by Joe of loath on 2011-04-07
You will need to forward port 80 for basic web services, as well as 22 if you use SSH, 443 if you use HTTPS, 43 if you use FTP.

---

### Post by macmike on 2011-04-07
That might have done the trick. I don't know if I can get it outside my local network yet. I can put in [www.mikealrhughes.com](www.mikealrhughes.com) now and get it to show up. If you try the site let me know if it works.

Thanks,

Mike

---

### Post by crispy_420 on 2011-04-08
Works for me. May have been a temporary glitch for you.

> **Joe of loath said:**
> 43 if you use FTP.

FTP runs on 21 (and 20 to real technical) I believe.

---

