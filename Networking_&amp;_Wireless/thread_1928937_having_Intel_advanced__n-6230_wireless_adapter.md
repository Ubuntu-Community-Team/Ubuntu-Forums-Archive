---
title: "having Intel advanced  n-6230 wireless adapter"
date: 2012-02-21
forum: Networking &amp; Wireless
---

### Post by manu7889 on 2012-02-21
i am new to linux installed unbuntu 10.04 on my laptop having intel advanced centrino N6230 wireless interface . after installation of ubuntu network module has had exclamation mark
when i tried troubleshooting wireless 
as per instruction i typed 
 
lshw -c network 

its showing unclaimed network

what to do
next plz help me
out

---

### Post by wildmanne39 on 2012-02-21
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

