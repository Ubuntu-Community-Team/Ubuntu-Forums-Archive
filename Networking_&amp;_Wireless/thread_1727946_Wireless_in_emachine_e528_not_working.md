---
title: "Wireless in emachine e528 not working"
date: 2011-04-13
forum: Networking &amp; Wireless
---

### Post by Gotlieb on 2011-04-13
Hi Everyone,

Firstly, I am a total newbie to Ubuntu. I just replaced windows 7 ultimate with ubuntu 10.04. The problem is I cannot detect wireless anywhere I go and network manager is only works well when a network cable is sticked in. Can you please help? Am I missing certain extensions like that? I really need my wireless to work.

Thanks :confused:

---

### Post by chili555 on 2011-04-13
Congratulations and welcome to the party! Please open Applications > Accessories > Terminal and run:```
lspci -nn
```Post the result, or, if you can see the particular line that is your wireless card, post that one line. Thanks.

---

### Post by Gotlieb on 2011-04-29
Thanks, that solved it.

---

