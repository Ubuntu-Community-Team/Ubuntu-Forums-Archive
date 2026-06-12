---
title: "[SOLVED] RTL8139 Ethernet not working"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by gletob on 2009-01-03
Hi I just installed ubuntu on my desktop and it has an integrated ethernet controller the Realtek RTL8139 and it's not working.  The cable is connected but the lights on the back of the computer and on the router are not on.  The card and cable work fine in XP.  lspci shows it as 
```
02:03.0 Ethernet Controller: Realtek Semiconductor Co., Ltd. RTL8139/8139C/8139C+ (rev10)
```

---

### Post by albinootje on 2009-01-03
> **gletob said:**
> Hi I just installed ubuntu on my desktop and it has an integrated ethernet controller the Realtek RTL8139 and it's not working.  The cable is connected but the lights on the back of the computer and on the router are not on.  The card and cable work fine in XP.  lspci shows it as 
```
02:03.0 Ethernet Controller: Realtek Semiconductor Co., Ltd. RTL8139/8139C/8139C+ (rev10)
```

Please try this :
[http://wiki.archlinux.org/index.php/Configuring_network#Realtek_No_Link_.2F_WOL_issue](http://wiki.archlinux.org/index.php/Configuring_network#Realtek_No_Link_.2F_WOL_issue)

> 
Method 2 - Enable WOL in Win driver

Probably the best and fastest fix is to change this setting in the Windows driver. This way it should be fixed system wide and not only under Arch (eg. live CD's, other OSes). In Windows under device manager, find your Realtek Network adapter and double click it. Under the advanced tab change "wake-on-lan after shutdown" to enable.

 In Windows XP (example)
 Right click my computer
 --> Hardware tab
   --> Device Manager
     --> Network Adapters
       --> "double click" Realtek ...
         --> Advanced tab
           --> Wake-On-Lan After Shutdown
             --> Enable.


---

### Post by gletob on 2009-01-03
Thanks so much that fixed my problem!

---

### Post by bro-ken on 2010-03-31
what about this problem in Karmic with same adapter?

---

### Post by Dener on 2010-04-09
What about if I don't have xp just Ubuntu 9.10?

---

### Post by Iowan on 2010-04-09
There are a few RTL8139 threads... If none of them help, you might start a new thread. This one is marked [SOLVED], so it may not draw the assistance you hope.

---

