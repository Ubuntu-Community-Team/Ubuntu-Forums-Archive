---
title: "NIS passwords fail to authenticate"
date: 2010-04-28
forum: Networking &amp; Wireless
---

### Post by MrtnLowr on 2010-04-28
Hi All,

Ok, though I'm new to Ubuntu I've been a Solaris administrator of a small network for many years.

I've searched the forum on this issue, finding several reports of similar situations but it doesn't appear anybody has posted  a solution.

I have a small domain of Sun machines running Solaris 9 with host & user info kept on one machine acting as a NIS+ server.  I now have a new core I7 machine with Ubuntu 9.04 installed and I want the users to have transparent access to their Sun data without creating new accounts.   Following the SettinupNISHowTo I installed YP (a.k.a NIS) and autofs, modified nsswitch.conf appropriately (including adding a 'publickey: nis' line), and demonstrated that they are both working correctly.  Unfortunately when I try to login as a Sun domain user I get an incorrect username or password message.  If I login using the Ubuntu installer's account I can use ypcat to see all the database tables and I can also automount home directories from the Sun domain.  So why does the login fail?

Any help as to where to look for further info or how this can be fixed would be much appreciated.

Cheers!

---

