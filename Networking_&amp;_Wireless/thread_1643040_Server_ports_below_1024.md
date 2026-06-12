---
title: "Server ports below 1024"
date: 2010-12-11
forum: Networking &amp; Wireless
---

### Post by sv1jsb on 2010-12-11
Hi all, I have recently upgraded to 10.04 and I am trying to access my apache and sshd servers from the net but I have not succeed so far when those two are using their regular ports.
If I change their ports to something greater than 1024 they work fine.
80->8010 
22->4567
(I can access the servers when I am connecting from local net: 192.168.1.0/24) 
Is this restriction build into the new kernel? 
Is there something I can do to fix this without recompiling the kernel?  
Any input is welcome
Thank you very much,
Andreas

---

### Post by iponeverything on 2010-12-11
This seems like something your ISP is doing. Often they restrict the standard server ports to force people to buy a commercial account if they wish run a server. The fact that you can reach the services from your internal /24 shows that the server itself is not restricting the traffic.

---

### Post by sv1jsb on 2010-12-11
Well this isn't the case because it worked fine with karmic about a week ago.
The problem arose when I upgraded to lucid.

Andreas

---

### Post by iponeverything on 2010-12-12
> **sv1jsb said:**
> Well this isn't the case because it worked fine with karmic about a week ago.
The problem arose when I upgraded to lucid.

Andreas

It would have been useful information to include in your initial post, unless you just like to be vague. 

regardless, I would remove any iptables rules that you have as that might be the cause.

---

