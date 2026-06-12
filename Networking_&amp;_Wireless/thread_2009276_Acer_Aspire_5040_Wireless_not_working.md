---
title: "Acer Aspire 5040 Wireless not working"
date: 2012-06-24
forum: Networking &amp; Wireless
---

### Post by mrlman on 2012-06-24
I got an old laptop from the Acer Aspire 5040 series that I recently installed ubuntu on and everything but the wireless works perfect on it. 
The laptop was running Windows XP before, and the wireless worked fine there and you could activate/deactivate it with a button, the button does nothing in ubuntu.
I have tried changing kernel and other various fixes without any success.
From what I've read, this issue is common in 12.04  and I would really want it to work, so I won't have to use an older version of ubuntu.
The network card is an Atheros AR5005g

Is there any way to get it working without having to use an older version of ubuntu?

---

### Post by wildmanne39 on 2012-06-24
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

