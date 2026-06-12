---
title: "Stange issue with wireless network at university"
date: 2006-06-20
forum: Networking &amp; Wireless
---

### Post by l.tambiah on 2006-06-20
Hi folks,

Had a strange issue over the past week, which I have now resolved a fix for, but would like extra information so I can understand what is going on. Any advice would be appreciated...

Last week I had my Ubuntu Dapper machine in Uni but only to find that when ever I launched Firefox I would wait a long time (like 3-4 mins) before the page would load and offer me a login to the uni's wireless network. Most often the browser would crash. This was Strange as my machine worked fine at home on my own wireless network. 

I gathered that my resolv.conf adds required nameservers for my home network which is correct. When I enter the university it keeps the same nameserver entries from home and adds "search ticwireless.local" hence why it gets confused. Why doesn't it remove my home entries?

I can resolve this issue by editing the /etc/resolv.conf when im at university. I simply remove the nameserver entries generated from my home network and leave the line "search domainname" (which is generated from the unis wireless network) and all is fine. 

However I have to do this everytime I go to the uni. It should be noted that the university uses a proxy my home wireless network does not.

Does anyone know why this is happening?

Redirecting to [Wi-Fi Radar Thread]("http://www.ubuntuforums.org/showthread.php?t=202480")

---

