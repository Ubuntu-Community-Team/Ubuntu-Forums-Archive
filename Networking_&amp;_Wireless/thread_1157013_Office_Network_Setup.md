---
title: "Office Network Setup"
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by Chetan26 on 2009-05-12
Hi ,
       I have  got 4 ubuntu machines and one windows machine to be connected in a network. I have installed Samba on one of the Ubuntu machines. But Iam not able to view all my computers in the networK.
I can see only 2 machines on network from a ubuntu machine , 1 windows and 1 ubuntu iam on.

what  addtional settings do we need to bring all the 5 machines under the same network?

Pls  provide help , Iam struck .


Thnx
Chetan

---

### Post by Iowan on 2009-05-12
All machines will need to be in same workgroup.  In Ubuntu, that's in /etc/samba/smb.conf... although the workgroup can be set under System>Administration>Network on this Gutsy box (cannot find it on my Jaunty laptop).  Probably only machines with available shares will be displayed - and it may be necesary to install Winbind (and adjust /etc/nsswitch.conf) to see them by name.

---

