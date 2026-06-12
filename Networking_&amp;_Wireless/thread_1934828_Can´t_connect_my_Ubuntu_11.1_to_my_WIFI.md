---
title: "Can´t connect my Ubuntu 11.1 to my WIFI"
date: 2012-03-02
forum: Networking &amp; Wireless
---

### Post by palmaone on 2012-03-02
Hello hopping someone can help with my internet issue. 

My problem started last night, I could not connect to internet. In the mornning I restarted my router and same thing. So I tried different stuff from forums but have not been able to solve it. I found out that I can connect to other wifi networks (neighbors) and with my wife`s laptop and other devices connection to my wifi netwk works just fine.

My pc is 32 bit running ubuntu 11.10, I tried changing DNS settings for the network but it does not work...  I suspect the last update did the bad trick...

Help please

---

### Post by praseodym on 2012-03-03
Try to shut anything off the current completely for 15 minutes. If it is a laptop, take out the battery, too. After that please show:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```

---

