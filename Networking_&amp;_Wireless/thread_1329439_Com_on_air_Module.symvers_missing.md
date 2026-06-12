---
title: "Com on air Module.symvers missing"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by ASTRAPI on 2009-11-17
Hello

I was trying to install the com on air pcmcia on Backtrack and when i run this: 
svn co [https://dedected.org/svn/trunk](https://dedected.org/svn/trunk) dedected
cd /dedected/com-on-air_cs-linux
make && make -C tools


```
WARNING: Symbol version dump /usr/src/linux-source-2.6.29.4/Module.symvers
           is missing; modules will have no dependencies and modversions.
```

How can fix this missing Module.symvers?

Thank you

*They recommend:

> install a package libpcap-dev or the like

I was search at synaptic but no libpcap-dev ....

How i can do that as i am linux noob?

---

