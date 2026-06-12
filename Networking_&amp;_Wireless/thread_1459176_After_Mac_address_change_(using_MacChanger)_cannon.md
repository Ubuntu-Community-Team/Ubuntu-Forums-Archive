---
title: "After Mac address change (using MacChanger) cannont connect to the router."
date: 2010-04-21
forum: Networking &amp; Wireless
---

### Post by Snoreis on 2010-04-21
Hello,

After trying to change my mac address using macchanger, I've run into a problem. 

I successfully change my mac address as told: 
```
# macchanger eth1
Current MAC: 00:40:96:43:ef:9c [wireless] (Cisco/Aironet 4800/340)
Faked MAC:   00:40:96:43:ef:9d [wireless] (Cisco/Aironet 4800/340)
```

And then run ifconfig:
```
# ifconfig
eth1      Link encap:Ethernet  HWaddr 00:40:96:43:ef:9d 
...
```
Thus successfully showing my mac address has changed, however, after this I am no longer able to connect to my router (wireless, linksys wrt150n, running dd-wrt).  Would a simple restart of my computer fix the problem (I've already restarted the session, no positive result), or is this a problem that needs to be dealt with in the router its self?

Thanks,

---

### Post by kirb3 on 2010-06-11
This has happened to me as well when trying to change the MAC address for a Linksys USB wireless adaptor.  I can't remember the model number (I already returned it because it never could connect after I changed the MAC), but it's the really popular one, WSUG<something>.  I'm not sure what causes the issue, unfortunately; I had some people from my dorm who are really good with Linux (one had done some kernel hacking, etc.) and none of them could figure it out, either, so it must be pretty tough to fix.

---

