---
title: "No network in VMware Player"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by kaffelars on 2006-07-08
I have installed VMware Player to try out PC-BSD, and it runs fine, except that the network is unavailable. I use eth1 (wireless) at home, and I suspect that VMware uses eth0, but I can't find any settings.

Anyone with suggestions?

---

### Post by mips on 2006-07-08
If I recall correctly their is an option in vmare to bridge the two adapters either from the menu or during installation.

---

### Post by kaffelars on 2006-07-08
Hmm, I am not sure what installation you are referring to. I installed VMware Player through apt and downloaded a VMware image of PC-BSD (which I use on VMware Player on my Windoze box).

---

### Post by mips on 2006-07-08
Maybe I'm thinking of the Server version which is also free but has more features than the player.

---

### Post by vkohli on 2006-07-09
Yes you are thinking of the workstation version. If you download vmware workstation you will be able to setup several different types of networks (i.e. bridge, NAT, host-only, etc..). 

Cheers,
vkohli

---

### Post by mips on 2006-07-09
I think the server version (which is free unlike workstation) also has these features.

---

### Post by kaffelars on 2006-07-09
I can't see why the (free) Server Version couldn't be used to run a standard desktop OS, so I can give that a try :)

---

### Post by mips on 2006-07-09
> **kaffelars said:**
> I can't see why the (free) Server Version couldn't be used to run a standard desktop OS, so I can give that a try :)

It works very well, used it before and ran BSD on it.

---

### Post by kaffelars on 2006-07-09
Sounds great, got a bit overwhelmed by the registration form but I guess it's worth it :)

---

### Post by kaffelars on 2006-07-11
VMware Server did the job :-D 
I wasn't aware of the free server edition's vast superior features and settings, compared to the Player. It also seems to run faster on my 1,7GHz Pentium M laptop running Ubuntu than on my Pentium D 2,8 GHz desktop running Win XP :-D

---

