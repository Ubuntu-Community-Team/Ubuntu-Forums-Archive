---
title: "Ubuntu causes work Laptop VPN to drop"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by mbspark on 2009-09-23
I have the most bizarre problem happening now.

I work from home and run my work laptop side-by-side with my personal pc. I've recently come back to ubuntu (running 9.04) and now when doing any type of large download, new linux iso's streaming tv shows on the personal linux box, it causes my vpn on my work XP to drop.

I've been running xp on the desktop before ubuntu and never had an issues. I went back and forth today downloading the same files. XP no problem with work VPN, ubuntu kills it every time.

Any ideas?? I love linux and hate having to keep going to back to XP.

---

### Post by mbspark on 2009-09-24
Update:

It seems this is only the case when connecting wirelessly with Ubuntu.

Is there something missing with the Wireless configuration? I was thinking I may submit a bug. Wireless is 3-4x slower than wired and it's causing other connections to drop vs wired.

---

### Post by doas777 on 2009-09-24
ok, we have teh same problem using wifi/broadband cards with Cisco VPN client on windows. 

basically, aircard/wifi are jittery bursty connections that experience vast changes in latency and usable bandwidth from one second to the next. it's fine for loading a page, but a constantly on protocol will not work well with it.

VPN is a tunneling encryption protocol that is not very tolerant of latency, and requires a consistent response in a timely fashion. if the response does not come in time, the encryption fails and the connection is terminated.

so short answer VPN + Wifi = Fail.

My feild staff are having all kinds of trouble with their broadband cards when hitting internal resources, and they have to disconnect from the VPN when connecting to public facing web apps that we created for them, or we are looking at 10 secs per repost/submit.

---

