---
title: "Dell laptop latitud d600 no wireles"
date: 2012-01-21
forum: Networking &amp; Wireless
---

### Post by martel123 on 2012-01-21
hello, im a newbi and dont know nothing at this i install it in my laptop and now my wireles is not working does anybody can help me im new to this so be gentle on me thank you:popcorn: my laptop is a dell latitud d600

---

### Post by wildmanne39 on 2012-01-21
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

