---
title: "no man is an island..."
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by hivoltage on 2009-01-06
I'm running Ubuntu 8 and am unable to ftp/ping/vnc to my system even from my own LAN.  I believe that I have iptables turned off, and my ftp server is running.  I  have even tried playing with port redirect on my router.  No luck.  What step have I forgotten? TIA.

---

### Post by Iowan on 2009-01-06
Ubuntu 8 has two versions - 8.04 (Hardy) and 8.10 (Intrepid).  From the Ubuntu box, check a few things: What are results of **ifconfig -a**?  Can you ping "localhost" or your ip address (as revealed by **ifconfig**)?

---

