---
title: "Instant Discovery of Apache 2 WebDAV Shares using Avahi?"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by vessuvius81 on 2006-06-10
I run an Ubuntu 6.06 home server (I did the LAMP install), but the primary machines on my network are Macs running OS X. I like to use webdav for fileshares on the Ubuntu server, using Apache 2. That makes it easy to connect to the shares through OS X's Finder--but not as easy as it could be. 
I would like the shares to show up in OS X's Finder under "Network" automatically via Bonjour/Zeroconf.

I've seen a how-to on this at:
[http://www.fatalistreview.com/?p=75]("http://www.fatalistreview.com/?p=75")
but it has several misstatements and I haven't been able to get the webdav shares to show up automatically in Finder. 

There is also some information at:
[http://0pointer.de/lennart/projects/mod_dnssd/]("http://0pointer.de/lennart/projects/mod_dnssd/")
but I have had no luck.

Does anyone know a good how-to or would be willing to write one up on how to configure apache 2 and avahi to cause webdav shares to show up via bonjour/zeroconf to Macs on the local network?

---

