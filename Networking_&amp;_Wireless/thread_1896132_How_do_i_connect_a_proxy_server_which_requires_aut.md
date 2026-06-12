---
title: "How do i connect a proxy server which requires authentication?"
date: 2011-12-16
forum: Networking &amp; Wireless
---

### Post by javad74 on 2011-12-16
Hi all
Two days ago i installed Ubuntu 11.10 and deleted Windows to enjoy Ubuntu and the world of free software when i came here i found this world very very interesting but i have one BIG problem:I can't use my proxy service here:(
When i was on Windows 7 i bought a HTTPS proxy.the service provider gave me a username and password and a software called proxifier.
I put the proxy address,port,username and password BUT when i came here i put the address and the port and i wanted to put the username and password but there is not such place for that.
How the hell should I connect to this server with ubuntu 11.10?
Thanks

---

### Post by loolooyyyy on 2012-03-23
kind of an old thread, but i dont want anyone to leave the opensource world!!
use proxychains, tsocks
set your proxy information directly in your app, i.e firefox, it will ask for passwors/username at  the beginning itself

use this form:
User:pass@Ip in network settings in ubuntu
(i donnow maybe pass:user? nah... user:pass)

---

