---
title: "Computer broadcasts wrong name"
date: 2012-09-26
forum: Networking &amp; Wireless
---

### Post by tim042849 on 2012-09-26
I have a computer on my network that is broadcasting the wrong name to the network.
I.E. The computer name is **barbara**. It is seen on the network (and by the router),
as **hpmini**.

The computer has ubuntu 10.4 as the OS. IP is static. When I ping **barbara** from my mac,
I get the response with the correct IP. I can access **barbara** from my mac, using the
both smb://barbara/sharename and smb://hpmin/sharename , but it shows up in the network browser and linux
network browsers as **hpmini**. How can I correct this?
thanks
tim

---

### Post by tim042849 on 2012-09-26
Well, I jumped the gun here. I have limited access to this machine, but grepped
/etc for **hpmini** and found in /etc/samba/smb.conf "hpmini" was assigned 
to **netbios name**. All is good now. Even tho I was premature in my request,
perhaps this posting might help someone else.
cheers
tim

---

