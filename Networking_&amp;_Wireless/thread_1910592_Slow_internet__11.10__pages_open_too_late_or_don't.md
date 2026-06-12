---
title: "Slow internet  11.10 : pages open too late or don't open at all"
date: 2012-01-17
forum: Networking &amp; Wireless
---

### Post by ubermonkeys on 2012-01-17
Hello. 
Whenever I open a new page, it takes ages for the page to load, sometimes it doesn't even open.
I've came across several solutions on Ubuntu Forums, yet none has solved mine. Btw, I am not a pro in terminal. 
I have a TOSHIBA a200-1bp and I only use ubuntu 11.10 (seems like it is smoothly working except this problem) as OS. 

Thank you for your answers!

---

### Post by wildmanne39 on 2012-01-17
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

