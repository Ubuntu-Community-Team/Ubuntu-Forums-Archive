---
title: "Network failed after routine update, 10.10 - 64bit"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by susanto on 2011-03-22
I have recently do a software update (Ubuntu 10.10, 64 bit)
as recommended, and now having problem with internet connection.

This machine is connected to a local router (CISCO SOHO).
The static IP setting works fine and recognised by other 
machine (PING ok from other machine). But no internet
connection, while other machines have no such issue.

I found out that the resolv.conf didn't have the name server.
Manually editing this solve the internet connection.
Upon shutdown, it seems network manager override the file and
delete the configuration.
After a restart, internet is down again until I manually 
rewrite the resolv.conf file.

Is there any setting that I need to add to resolve this issue?

---

