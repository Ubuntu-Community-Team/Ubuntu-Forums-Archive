---
title: "Do I need bridging or not ?"
date: 2011-05-30
forum: Networking &amp; Wireless
---

### Post by hanslammerts on 2011-05-30
Hi there,
 
I'm trying to set up a high available LAMP server, and saw already a couple of good howto's. All of these solutions use a minimum of two network adapters on one physical machine. I do have two physical machines, that both have one ethernet adapter and one wireless adapter. Since I find networking rather complex, I get stuck in this fase of the design.
 
Can I just use the ethernet controllers on both machines to do the actual networking for the LAMP server, and use both wireless adapters for the network heartbeat between the two servers ? 
 
If I would configure the ethernet adapters in, say, the 192.168.2.x network, and the wireless adapters in another network (say 10.0.0.x), I would be needing a separate wireles router/AP for this to work, right ?
 
Why would I want to have two different networks anyway ? (all docs use this...)
 
If I were to install LAMP on both physical servers in a virtualized environment, would I need to bridge both the ethernet and wireless adapters, or just the ethernet adapters, since they will be the only adapters talking to the outside world ?
 
I have been searching for weeks for a more or less simple explanation for my problem, but haven't been able to find anything clear. In fact, I'm more confusaed now than when I started Googleing....
 
Hope someone can help me out.
 
Thanks,
Hans

---

### Post by hanslammerts on 2011-06-01
Bump.
 
No one ? Please ?

---

### Post by lisati on 2011-06-01
I use just one machine with one network card and no wifi card to host my server. Other than it being a bit slower than I'd like at times (it's a few years old), it works well enough most of the time.

---

