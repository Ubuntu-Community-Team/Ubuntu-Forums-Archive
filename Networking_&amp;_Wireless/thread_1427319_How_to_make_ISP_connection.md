---
title: "How to make ISP connection?"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by thairsadi77 on 2010-03-11
plz help me 
i cant make the isp connection in linux ubuntu 9.10
i am new to this and i swear to god i will never try linux ever if i cant connect to the internet so all i need is that how i can connect to internet .
i am using linux for 6 days now and i am using another computer to post this using windows xp
my system recognize well all the drivers including lan card but i dont know how to made the isp
plz help

---

### Post by Iowan on 2010-03-11
> **thairsadi77 said:**
> i am new to this and i swear to god i will never try linux ever if i cant connect to the internet Threats are unnecessary...
From a terminal:```
ifconfig -a
```Post results - if there is no IP Address, check:
```
sudo lshw -C network
```

---

