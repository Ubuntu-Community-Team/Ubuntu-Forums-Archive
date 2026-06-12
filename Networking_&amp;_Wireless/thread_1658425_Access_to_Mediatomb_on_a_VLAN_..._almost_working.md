---
title: "Access to Mediatomb on a VLAN ... almost working"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by mebunto on 2011-01-02
[FONT=Arial][SIZE=2]Hello, I have installed Mediatomb successfully, I have two  networks - an ISCSI storage network on 192.168.2.nn that is the DROBOPRO only and the Internet  network on 192.168.0.nn which has the rest of my LAN.  Mediatomb has found the correct folders on the  ISCSI storage and I have configured it so that the Mediatomb browser interface is called up on 192.168.0.11:49152

The Internet connected computers devices can browse to that page [/SIZE][/FONT][SIZE=2]however I cannot stream the files.  When I try to stream the file, it serves them from 192.168.2.81:49152/content/media/object_id/4194/res_id/0

So I am assuming that there is a problem with the network route to that VLAN ..... am I right?  If so, what should I do?  Do I need to set a VLAN bridge on the server?

Anything would be helpful.

Thanks
[/SIZE]

---

### Post by mebunto on 2011-01-02
sorry to be impatient - perhaps someone will pick this up

---

### Post by mebunto on 2011-01-03
Well, it all suddenly started working without making any changes ... I don't know why.

---

