---
title: "peculiar doubt on iptables with NAT"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by codingfreak on 2009-10-07
Hi,

I am new to iptables and NAT terminology. I got a strange problem regarding writing rules for my setup while using NAT.

Let us assume I have Machines 'A' and 'B' in my private network and they are connected to internet via Linux Server. I just have one Public IP-address and I have to use NAT.

My doubt is ... Let use assume if I am accessing yahoo.com from my private Machines 'A' and 'B'. As we are using NAT postrouting is done in iptables and since I have a single public address how does the YAHOO server differentiate between my private machines A and B ???

So can anyone tell me the iptables rule where I should be able to differentiate the traffic from Machine 'A' and Machine 'B'.

---

