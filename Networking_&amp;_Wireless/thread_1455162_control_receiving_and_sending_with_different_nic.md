---
title: "control receiving and sending with different nic?"
date: 2010-04-15
forum: Networking &amp; Wireless
---

### Post by hansyin on 2010-04-15
hi,

For a special test, I need my pc receiving packet with one IP but reply(sending) packet with another IP.  I'm not sure if it's doable. 

My PC(PC1) has two network cards, say eth0 with ip0 and eth1 with ip1.  I launch a ping (I also tried other application) from another PC(pc2) with source IP2 and destination IP is ip0. Then I add a static route on pc1 to direct traffic to ip2 to go through interface eth1. 

I already saw packet reaches eth0 of pc1 but somehow it get dropped immediately. I hope it can send reply from eth1 interface. 

I tried to setup rp_filter,ip_forwading but still fails. 


Could anybody give me an answer? thanks.


Hans

---

