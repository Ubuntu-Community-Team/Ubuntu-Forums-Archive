---
title: "Multicast Problems"
date: 2011-06-28
forum: Networking &amp; Wireless
---

### Post by dkeeper09 on 2011-06-28
Hey guys,

I am trying to multicast using the open source program FOG. Idk if anyone has heard of it, but it is like Ghost or Clonezilla. I can't seem to multicast properly, but I think it is because my clients aren't getting packets. 

From my Ubuntu machine, I run:
udp-sender --file /opt/fog/log/multicast.log --ttl 32

Then from two test clients, I run:
udp-receiver --mcast-rdv-address xx.xx.xx.xx

On the server I get the output:
Bad command 0200
Timeout notAnswered=[0,1] notReady=[0,1] nrAns=0 nrRead=0 nrPart=2 avg=10205

and it repeats the Timeout line. Does any one know what could cause this? 

Thank you very much.

---

