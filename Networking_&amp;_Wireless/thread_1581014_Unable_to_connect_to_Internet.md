---
title: "Unable to connect to Internet"
date: 2010-09-24
forum: Networking &amp; Wireless
---

### Post by saurabhgeo on 2010-09-24
I have dual boot system and on windows I am able to connect to wireless but on Ubuntu I am not able to connect to wireless.

I desire to learn to trouble shoot the problem my self hence I would appreciate if some one guides me How to look for the problem.
and how to find what is wrong and right 

That is why I am not posting any output here but rather would like to learn to solve the problem by myself


Best Regards

---

### Post by Iowan on 2010-09-24
From a terminal, **ifconfig -a** will show if your interface(s) get an IP address. **sudo lshw -C network** will provide more information on your interface(s).

---

