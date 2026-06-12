---
title: "Probems with Buffalo WLI-U2-KG125S wlan card &amp; ndiswrapper"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by Z0d1@c on 2009-04-03
I tried to install the drivers from my desktop (the code says "Työpöytä", the same in Finnish) using [this]("http://ubuntuforums.org/showthread.php?t=370589"), but it won't work:

```
matti@Kotikone:~$ cd /home/matti/Työpöytä/U2KG125S
matti@Kotikone:~/Työpöytä/U2KG125S$ sudo ndiswrapper -i netg125.inf
[sudo] password for matti: 
couldn't open netg125.inf: No such file or directory at /usr/sbin/ndiswrapper line 219.
matti@Kotikone:~/Työpöytä/U2KG125S$ 

```

Anyone know what is wrong with this?

---

### Post by Z0d1@c on 2009-04-05
Got this already to work by moving to Ubuntu 8.10 which had the rndis_wlan drivers installed as a default. The card works perfectly now.

---

