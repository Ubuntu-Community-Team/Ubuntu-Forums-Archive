---
title: "Printing problem via samba"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by roadtodebian on 2011-11-09
I've 2 computers. Computer A installed with ubuntu 7.10 and samba. I shared some folders and also one printer. 

Computer B also installed with ubuntu 7.10, and i want to use printer from computer A. When i try to adding the printer, it show up with password dialog. I'm confused which password the system needed. I try entered user password and root password, but failed.

[IMG]http://i42.tinypic.com/b7x36w.png[/IMG]

Thx for your help..

---

### Post by RedSingularity on 2011-11-10
How about the password for the user on the machine you are CONNECTING TO.  Not the local one.  Does that work?

---

### Post by faflu on 2011-11-10
Looks like it asks for a password of user 'kpdw' on the machine you're adding the printer. So you must type in the correct password for this user. The problem could also be that 'kpdw' is not allowed to install printers - it needs to belong to 'lpadmin' group.

---

