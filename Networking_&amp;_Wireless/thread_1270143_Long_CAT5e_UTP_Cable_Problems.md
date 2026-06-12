---
title: "Long CAT5e UTP Cable Problems"
date: 2009-09-19
forum: Networking &amp; Wireless
---

### Post by linuxus95 on 2009-09-19
Hi, and thanks for any help. I am currently running two Ubuntu machines, both with Jaunty, on my home network. My first computer is in my room, right beside a Linksys WRT54GL router. This computer is connected to the router via a short, Cat5 UTP cable. The other computer, however, is in the room below, and is connected to the router using a solid, 20 metre, Cat5e straight UTP cable. For some strange reason, it will not obtain an IP Address from the router. If I bring the computer up to the router and connect it with a short CAT5 cable, the connection works perfectly. Strangely enough, when I use a Windows Vista laptop with the long Cat5e cable, it will get the IP adress from the router and it will work perfectly. I am not really sure if this is a problem with Ubuntu, or if it is just a problem with the cable.

Thanks for any replies.

---

### Post by bkratz on 2009-09-19
> **linuxus95 said:**
> Hi, and thanks for any help. I am currently running two Ubuntu machines, both with Jaunty, on my home network. My first computer is in my room, right beside a Linksys WRT54GL router. This computer is connected to the router via a short, Cat5 UTP cable. The other computer, however, is in the room below, and is connected to the router using a solid, 20 metre, Cat5e straight UTP cable. For some strange reason, it will not obtain an IP Address from the router. If I bring the computer up to the router and connect it with a short CAT5 cable, the connection works perfectly. Strangely enough, when I use a Windows Vista laptop with the long Cat5e cable, it will get the IP adress from the router and it will work perfectly. I am not really sure if this is a problem with Ubuntu, or if it is just a problem with the cable.

Thanks for any replies.


Here is what I found "

Everything all the way from Cat3 was ALWAYS 4 pairs of twisted Wires
Cat 5 is 100BaseT (100 Mbps w/ 100 m range)
Cat 5e is 1 Gbps (1000 Mbps) w/ a 75m range

Cat 5e ONLY has a 100m range if you get Base-TX. (Not base T)
Cat 6 is 100m and supposedly can do over 1.2 Gbps but...thats the spec.

That's the real, hard specs. No room for interperation or arguement. I'm reading it straight out of the 2006 Comp TIA book. "

---

### Post by linuxus95 on 2009-09-19
Thanks a lot for your reply, I will probably have to invest into a cat6 cable.

---

### Post by stinger30au on 2009-09-19
yep cables can cause some wiered errors

---

