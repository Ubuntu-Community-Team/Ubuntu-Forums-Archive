---
title: "Ubuntu connects to wireless router but pages don't load"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by doctor whom on 2009-07-12
Hello all,

I have seen this issue on the net but without any solutions.
I installed Ubuntu 9.04 on a friends laptop. The wifi card was detected.
I created a new wireless in Ubuntu. Ubuntu says it's connected. The little bar icons are at full. When I go to a web page it won't load. My Ipod Touch connects on the same wireless effortlessly.
As a side note, when I plug the ethernet into the laptop from the same router, it isn't detected. Any solutions?

D

---

### Post by RedSingularity on 2009-07-12
Post the output of ifconfig.

---

### Post by anystupidname on 2009-07-12
You sure this isn't just a case of DNS problem? (assuming ifconfig shows you have an IP in the right range)
Can you ping your gateway (router's IP) and a public IP such as 208.67.222.222?
Check your /etc/resolv.conf

---

