---
title: "PPPoE on Wireless problem."
date: 2010-05-23
forum: Networking &amp; Wireless
---

### Post by Drycola on 2010-05-23
Hi,

I have an internet connection which is PPPoE by the wireless connection.
When I set it by pppoeconf it works, but once I restart the machine the wireless is no more 'managed' so I have to edit the '/etc/network/interfaces' file to remove any added information (except for the loopback).

Now whenever I need to connect to PPPoE I have to go through all the pppoeconf configurations again, it is really annoying, (and some non-professional users need to use it too!)

So, how can I set my pppoe to run smoothly on every startup? (without getting the 'wireless not managed' everytime) :???

---

### Post by Drycola on 2010-05-24
bump!

---

### Post by dineshs on 2010-05-25
1.Did you try to configure the connection via the `DSL tab' in Network manager.Please ensure that /etc/network/interfaces contain only  this before trying .
```
auto lo 
iface lo inet loopback
```  
2.Can you post the contents of
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
``` 
Ref [http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)
BTW There are modems/routers capable of storing your username and password given by ISP .If your modem/router supports this,you need not run pppoeconf everytime

---

