---
title: "can't able to connect with wireless in ubuntu10.04"
date: 2010-11-18
forum: Networking &amp; Wireless
---

### Post by valarmathi on 2010-11-18
[FONT=Times New Roman][SIZE=5][COLOR=black]hi all, [/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=5]i purchased a lenovo laptop and i installed windows 7 first. after a week i installed ubuntu10.04 which is really very useful. but, i can't able to connect with wireless internet in ubuntu 10.04. can i know what was the problem? can anyone help me to recover from that..;););)[/SIZE][/FONT]

---

### Post by dineshs on 2010-11-19
In a terminal (Applications-accessories-terminal)type 
```
sudo lshw -C network
``` enter and  post the output
Also```
iwconfig
```and```
ping 4.2.2.1 -c3
```

---

