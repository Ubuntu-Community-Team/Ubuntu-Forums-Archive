---
title: "Wifi is...where?"
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by cakeman007 on 2010-09-16
Hello! ):P

I have a MacBook Pro and I duel booted with Ubuntu 10.04 64bit. The only problem is connecting to my wifi. I cannot find the drop down menu to show me the nearby wifi. Any thoughts?

---

### Post by snowman4839 on 2010-09-16
It should be on the top bar on the right side.

if not...
post the output of
```
ifconfig
```and
```
iwconfig
```

---

### Post by cakeman007 on 2010-09-16
I cant take screenshot from Ubuntu because I dont have internet to post it! And i cant burn it to a flash drive because its acting up. For iwconfig it said just NONE NONE NONE for all of them

---

### Post by Iowan on 2010-09-16
Does **ifconfig -a** show a wireless interface? More details via **sudo lshw -C network**... even if you can't post them.

---

### Post by cakeman007 on 2010-09-16
none of these replies help. this is a UI problem.

---

### Post by chili555 on 2010-09-16
I believe my esteemed friend Iowan was asking for the output of these commands in order to help him diagnose the problem; not to fix the problem. I believe that wireless is not available because no driver has associated with your wireless card. In order to know how to find out what driver you need, Iowan needs some additional data. I suggest, even if you have to resort to a pencil, you post the result of these terminal commands:```
ifconfig -a
sudo lshw -C network
```Once he has analyzed the data, Iowan will know where to go next to get a driver going.

---

