---
title: "Problems with wireless connection"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by lencast on 2008-12-18
I just bought a Dell mini with Ubuntu oper.system, and although the computer finds my network and asks for the passphrase, it will not connect.  
I never used the Ubuntu oper. system, and I manually connected to the network, and was able to connect to the internet, but now I am afraid, that the system is not discovering any other network.  When I right click on the connection (the 2 computers icon) it will not show " Enable wireless network".  Since this computer does not have a cd/dvd drive, I am unable to reinstall anything.  I cannot log on to any other network, for it is not enabled, even if I authenticaded with password.

Anybody has any ideas how I can enable " wireless network" or even get it to show.

Thanks so much for your help.

---

### Post by S_e_P_p on 2008-12-18
Maybe you should update your system and look under Hardware drivers if you have an restricted hardware driver there.

Post the result of the following code here:


```
lspci -nn
```

```
lshw -C network
```

Greets,
SePp

---

