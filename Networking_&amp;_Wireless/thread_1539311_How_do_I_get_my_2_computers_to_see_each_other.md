---
title: "How do I get my 2 computers to see each other?"
date: 2010-07-26
forum: Networking &amp; Wireless
---

### Post by DEVIL DOG on 2010-07-26
I have a wired desktop running 9.10 and a wireless laptop running Ultimate Edition 2.6 (aka Ubuntu 10.04).  They both connect to a Netgear router.  I took down the firewalls on both computers and the router.  I also configured remote desktop to accept connections on both puters, but when I go to network all I see is Windows Network.  Click on that and I get "unable to mount".  I try remote desktop, but I get "connection closed".  I loaded a Samba configuration GUI prog, but I'm unsure how to use it yet.  Any suggestions?

---

### Post by Choad on 2010-07-26
it's pretty stupid, but you have to try and share a folder to prompt it to download the right network stuff. or rather that is what i have had to do in the past.

even then, it's pretty flaky in terms of being able to see the other computers. sometimes you have to find out the IP of the computer you want to connect to and type smb://1.2.3.4 in to the location bar of nautilus (where 1.2.3.4 is the IP of the machine you want to connect to)

---

### Post by DEVIL DOG on 2010-07-26
> **Choad said:**
> it's pretty stupid, but you have to try and share a folder to prompt it to download the right network stuff. or rather that is what i have had to do in the past.

even then, it's pretty flaky in terms of being able to see the other computers. sometimes you have to find out the IP of the computer you want to connect to and type smb://1.2.3.4 in to the location bar of nautilus (where 1.2.3.4 is the IP of the machine you want to connect to)

Thanks!  I'll try that out after I go to won hall and pay my taxes...  ugh.

---

