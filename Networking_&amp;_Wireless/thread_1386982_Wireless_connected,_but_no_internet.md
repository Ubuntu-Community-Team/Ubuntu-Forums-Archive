---
title: "Wireless connected, but no internet"
date: 2010-01-21
forum: Networking &amp; Wireless
---

### Post by gammax500 on 2010-01-21
Hello - after some frustrations, I was able to get my Broadcom 4322 installed and connected to my wifi network.  It's a DHCP connection and I can see my assigned IP address but I am not able to get to the internet.  I thought that must mean the DNS are not working, but if I try to bring up google.com by IP address it still doesn't work. Any suggestions on what I should look at?

I ran cat /etc/resolv.conf and see:

domain hsdl.wa.....
search hsdl.wa....
nameserver 4.2.2.1

But ping [www.google.com](www.google.com) gets
unknown host [url]www.google.com

---

