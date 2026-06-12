---
title: "No wireless connections detected"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by brijo77 on 2010-01-08
Hi all - first, I *must* apologize in advance - I'm not really computer saavy so please bear with me.

I installed Ubuntu onto my Dell Inspiron E1505 Laptop a few days ago and everything seems to be working smoothly - except that I have network connection.

I'm not sure how to resolve this - I'm certain that there's a wireless network card (?) because I was able to connect while I had Windows XP.

In the upper right hand corner, I have Enable Networking and Enable Wireless checked off, but it still won't connect to the internet.

I went into Network Connections and tried to Add the router that I'm currently using but still no success. I'm sure I'm missing a few basic steps and was wondering if someone could help me out.

Thanks.

---

### Post by Reglon on 2010-01-08
Same issue I think, i hover my mouse over the Internet connection icon in the top corner and it says "device not ready" for wireless.

---

### Post by Iowan on 2010-01-08
From a terminal, check (post) **sudo lshw -C network** - this should give some information about your network interface(s).

---

