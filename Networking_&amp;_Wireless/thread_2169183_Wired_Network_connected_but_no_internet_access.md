---
title: "Wired Network connected but no internet access"
date: 2013-08-20
forum: Networking &amp; Wireless
---

### Post by rpaterson on 2013-08-20
I installed Ubuntu 12.04 LTS on a Touchsmart Tx2, but when i connect wired to get the updates package to go Wireless, the signal is showing 
Connected and tell me Not Connected- working offline. 

Can anyone give me some insight on how to Fix this issue.

I am new to this Linux System, but have computer knowledge.

---

### Post by sanderj on 2013-08-21
What is the output of:

```
ifconfig
mtr -nrc2 8.8.8.8
```

Post the output here

---

### Post by rpaterson on 2013-08-21
Thanks you, by you saying ifconfig, Which i think u meant ipconfig, Anyway i had to manually config the network setting and "wallah" everything is working and getting update package. 
Thanks for the lightbulb.

---

### Post by howefield on 2013-08-21
> **rpaterson said:**
> by you saying ifconfig, Which i think u meant ipconfig,

ifconfig is a linux command, ipconfig is a windows command.

---

