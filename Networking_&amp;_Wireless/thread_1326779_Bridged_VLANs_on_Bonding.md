---
title: "Bridged VLANs on Bonding"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by Quetschke on 2009-11-14
Dear Community,


I'd like to create a configuration like this:


```
Virtual Interfaces
                  \
                   vbr1
                  /
eth0       bond0.1
    \     /
     bond0
    /     \
eth1       bond0.2
                  \
                   vbr2
                  /
Virtual Interfaces
```


On SUSE I had no problems to set this up. But now Ubuntu confuses me a bit...

Could anyone create an example "interfaces"-file for me, please?


Thanks a lot in advance.


All the best

---

