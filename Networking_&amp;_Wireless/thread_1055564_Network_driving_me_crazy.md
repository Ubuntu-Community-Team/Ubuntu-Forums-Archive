---
title: "Network driving me crazy"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by GuiGuy on 2009-01-30
My home network consists of four ubuntu 8.10 systems and on windows based notebook. 

The network had been working fine for several months. 

Several hours ago the Linux PCs were unable to access the internet. The Windows notebook worked fine. Local network access is fine for all PCs.

Since then I have googled, searched, read, checked hosts file, reset the router from cold, abused the ISP, rechecked hosts and DNS addresses. All around me reigns madness with the family complaining that they have no internet :(

I'm at wit's end, especially as the WinXP box has no trouble. Just the linux ones.

Is anyone able to give any further tips on what else I might try to resolve this?

PS: Please don't mention replacing Ubuntu with Windows. The  family is already onto me with that strategy ;)

Cheers

---

### Post by amarusrelor on 2009-01-31
I am having similar issues with my system as well.  Two days ago everything was perfectly fine and suddenly now nothing (firefox, pidgin, ssh) works.  I'm running a dual-boot with XP and it works fine.  It would be a great help if anyone has any insight into this problem.

---

### Post by Dr Small on 2009-01-31
How are the linux machines connected to the network? Ethernet or wireless? How is the windows machine connected to the internet? Ethernet or wireless?

Have you tried restarting network on the Linux machines?
```
sudo /etc/init.d/networking restart
```

Have you tried rebooting any of the linux machines?

Have you tried restarting the network router?

---

