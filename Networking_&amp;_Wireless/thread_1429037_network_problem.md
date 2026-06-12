---
title: "network problem"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by Mrenigma on 2010-03-13
Hi Guys i have a windows 7 on the other PC and i installed ubuntu on the laptop but i really need to access throe the network but i cant and i made the config for the smb.conf and i puted ENIGMA.NET the same as the windows 7 pc but still cant access any help please btw i have a router and i made the ip 69.69.69.69 if it helps thankkssss

---

### Post by Iowan on 2010-03-14
Capitalization and punctuation could use some work... but on the the problem. Why 69.69.69.69? There are 3 private address ranges - and that isn't in one of them. It might work, but could could problems later.
I haven't yet had opportunity to use Win7, so I'm not sure how to learn IP address, but **ifconfig -a** (from a terminal) should show the Ubuntu (laptop's) address. Once you know both addresses, you can try to **ping** from one machine to the other.

---

