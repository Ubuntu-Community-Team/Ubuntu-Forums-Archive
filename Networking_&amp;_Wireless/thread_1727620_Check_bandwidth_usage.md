---
title: "Check bandwidth usage?"
date: 2011-04-12
forum: Networking &amp; Wireless
---

### Post by fela on 2011-04-12
How do I check who / what is using all my upload bandwidth (and consequently my download bandwidth, due to the asymmetry of my connection)?

Thanks

---

### Post by Doug S on 2011-04-13
There was a similar thread a few days ago: [http://ubuntuforums.org/showthread.php?t=1719894](http://ubuntuforums.org/showthread.php?t=1719894) You might extract some ideas from that thread. Summary: Try tcpdump or wireshark to monitor the traffic to determine what is going on. I have used tcpdump for many many years, but I am relativley new to wireshark. Before writting this reply, I tried a feature in wireshark under "statistics" - "IP Addresses" that creates a list of IP addresses their number/percentage of packets.

---

### Post by ChrisWells on 2011-04-13
If you have a router that can use tomato firmware (or others) you can view bandwidth by network adapter, either in real time or total bandwidth. Not sure if it's the answer you're looking for

---

### Post by KegHead on 2011-04-13
Hi!

Try:

system..admin...system monitor...resources.

KegHead

---

### Post by fela on 2011-04-13
Hi, thanks for all the replies

I used netstat -av, which gave me some idea of what processes / ports were using bandwidth. Didn't try tcpdump/wireshark though, as the problem seems to have cleared itself up now (if it happens again I'll take all your advice though - cheers :))

---

