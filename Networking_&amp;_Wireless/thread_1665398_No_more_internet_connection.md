---
title: "No more internet connection"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by farfallanera on 2011-01-12
Hi, I've installed Ubuntu 10.04.01 with Wubi. Everything worked correctly untill I have updated some programs, than I can't boot, so I removed totally Ubuntu than I've installed it again. Now I can't connect internet, but I don't have any problem doing it when I boot in windows, and I remember that the first time I used Ubuntu it was all automatic and it connected without problems. Now it doesn't give any error just goes on asking me the password (I'm sure that the password isn't wrong) What should I do? Do you need other informations?

Thank you!!

---

### Post by snakebob on 2011-01-12
Your internet works in MS windows so physical internet connection is not doubtful.
 
But, I still do not know how you managed ubuntu installing process 
eventhough you decribed little.
 
however, I am sure there is not proper network setting because no more internet working.
 
1. First of all, please what ip address is allocated when ur ubuntu run
2. Then, also let me know setting value in "/etc/network/interfaces"

---

### Post by farfallanera on 2011-01-14
Thank you snakebob! I'd be glad to answer you but.... where can I find  that informations? :oops:
For the installation of ubuntu I just used Wubi, and followed the indications, nothing else

---

### Post by snakebob on 2011-01-14
> **farfallanera said:**
> Thank you snakebob! I'd be glad to answer you but.... where can I find that informations? :oops:
For the installation of ubuntu I just used Wubi, and followed the indications, nothing else
 
Please, use "text prompt terminal"
 
Then, type "ifconfig" then, you can find your IP address in running ubuntu.
 
Please, type "sudo vi /etc/network/interfaces"
Then, let me know what text were in there.

---

### Post by farfallanera on 2011-01-14
ok, after "ifconfig" I had  inet addr: 127.0.0.1 MASK 255.0.0.0
and after the other command I had "command not found"

Are bad news or good news!?

---

### Post by snakebob on 2011-01-14
> **farfallanera said:**
> ok, after "ifconfig" I had  inet addr: 127.0.0.1 MASK 255.0.0.0
and after the other command I had "command not found"

Are bad news or good news!?


IP 127.0.0.1 is not the address for internet.
As I expected, your network setting is abnormal.

to solve your issue, I need to know your setting value in /etc/network/interfaces 
/etc/network/interfaces is your network enviorment file

You can open and read/write it with VI editor
VI is basic editor in all LINUX

---

