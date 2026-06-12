---
title: "Beginner with DNS question"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by lmxac on 2009-06-18
Hello anyone,

I just started recently with Ubuntu or Linux at all for first time.  I am running 9.04.  I do NOT come from an open source environment so bare with me please.  I have figured some stuff out though :-)  Anyway, this is the only non Windows computer on our network.  We have a web based app on a 2003 server.  The server itself is on our LAN.  I can connect from XP to it by [http://servername:8080/Login.jsp](http://servername:8080/Login.jsp) with no problems.

When I do that from Ubuntu it tries looking for [www.servername.com]("http://www.servername.com")

/etc/resolv.conf looks correct

domain company.org
search company.org
nameserver 10.1.1.10
nameserver x.x.x.x  (external DNS name)

The two nameservers listed here are right and are the same DNS servers that  hundreds of computers use.  So I am stumped at the moment.  This may be a simple correction and am willing to be ridiculed for my open source nativiety :-)

Thanks in advance

Mike

---

