---
title: "Cannot connect to WEP network without connecting first in Windows"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by discord on 2010-02-15
Hello,

Sometimes I am unable to connect to my WEP network in ubuntu. No matter how many times I try, even restarting, it will not allow me to connect. However if I boot into XP, I can connect to the network. Then when I reboot again and then try in Ubuntu again, it will work. 


Router is a Netgear MR814v2

---

### Post by hansdown on 2010-02-15
Hi discord.

Network manager does some strange things... for instance, you can boot ubuntu, then reboot into ubuntu, and it will work.

Try installing 

```
wicd
```

It seems to work better.

---

### Post by discord on 2010-02-17
man f*** network-manager. Thanks for the advice, wish the devs would ditch that broken s***

---

