---
title: "Ubuntu, Fstab, and Freenas (Permissions)"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by mbranam1982 on 2009-09-26
I am trying to mount an SMB share from my freenas server on my ubuntu machine. I have added this line to my fstab:

//192.168.1.150/nas /media/Nas cifs admin,auto 0 0

when I BROWSE the share with smb://192.168.1.150/nas I can transfer files will full permissions:

drwxrwxrwx

in my mounted share files appear with the locked icon and the server says they only have this following permissions:

-rw-r--r--

how can I mount my share in fstab so It has full permissions without the locked ownership? to my knowledge the server has full read/write access to everybody (its only a home server)

Mike

---

### Post by amorfis on 2009-09-27
You can try to add to your line in fstab:

//192.168.1.150/nas /media/Nas cifs uid=user_id,gid=user_group,admin,auto 0 0

This way everything mounted by cifs belongs to user uder_id and group user_group.

You can check my blog about it:
[http://pawelstawicki.blogspot.com/2009/08/setting-samba-on-ubuntu-server-for.html](http://pawelstawicki.blogspot.com/2009/08/setting-samba-on-ubuntu-server-for.html)

---

