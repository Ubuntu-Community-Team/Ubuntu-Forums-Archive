---
title: "Can not connect with windows pc on the network"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by Marcelo Ramone on 2010-05-12
Hello,

I can not share documents with windows xp PC and Ubuntu 10.04 via crossed UTP cable (direct, without switch)

In xp the folders are ready to share and can be accessible from windows 7 with the same way.

I followed some tutorials from the web, for example:

$ sudo apt-get install samba samba-common smbclient winbind
 
$ sudo nano /etc/samba/smb.conf


; name resolve order = lmhosts hosts wins bcast


remove ";"


find: **[B]workgroup = WORKGROUP and change **"**WORKGROUP " to "INICIOMS" (that's the real network name** in this case )
[/B]

$ sudo nano /etc/nsswitch.conf


hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
add "wins"


and restart services: [http://ubuntuforums.org/showpost.php?p=7366839&postcount=10](http://ubuntuforums.org/showpost.php?p=7366839&postcount=10)


Also i made different changes in /etc/samba/smb.conf but is impossible access to XP pc...


Any suggestion?


Thanks in advance.

---

### Post by swerdna on 2010-05-15
This is wrong:```
name resolve order = lmhosts hosts wins bcast
```it should be like this:```
name resolve order = bcast host lmhosts wins
```
That's all the info we have to go on, so ohter things might be wrong. For a complete view of setting up Samba, see this tutorial:[http://ubuntu.swerdna.org/ubulanprimer.html](http://ubuntu.swerdna.org/ubulanprimer.html)

---

