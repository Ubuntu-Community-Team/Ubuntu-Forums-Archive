---
title: "SSH only works over wifi"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by Zilioum on 2009-09-13
I have 3 pc's. One notebook (A) , one server (B) and since yesterday a new desktop (C). 

My problem is that I cant ssh into  A from B and C if its connected via LAN, if its connected with wireless it works. If I try via LAN I get a "no route to host" error. nmap localhost on A showed that port 22 is open. 

The other way round its no problem. I can connect from A to B and C via LAN and wifi. 

Its a annoying because I want to sync A and C and for this wifi is a bit slow. 

Cheers

---

### Post by falconindy on 2009-09-13
Does the IP change when you go from wifi to wired? Are you accounting for this?

---

### Post by Zilioum on 2009-09-13
I knew that I had to be missing something fundamental (and stupid:D). It works now, thank you very much.

---

### Post by issih on 2009-09-13
just a little tip, in a local lan, you can use "hostname.local" rather than the ip address.

This uses avahi (bonjour) to resolve the ip address and therefore avoids these kind of issues.

Hope that helps

---

### Post by Zilioum on 2009-09-14
I did that. The problem was that I have a Dual Boot setup on my pc. When I installed Xp I gave it a different computer name (zilioum-xp instead of zilioum-linux). The weird thing is that even when I run ubuntu (which is almost always :P) and I am connected to my network via LAN the computer name is zilioum-xp. And since I assigned a static ip to that name, it didnt work either when I tried to connect via ip address (which was the one of zilioum-linux).
is there any way of having the same name for my pc on wifi and Lan? (and same IP? just asking, but I think this isn't possible)

---

