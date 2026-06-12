---
title: "how to share internet conection"
date: 2005-02-25
forum: Networking &amp; Wireless
---

### Post by Zarir on 2005-02-25
Hi
 I just instaled Ubuntu,and im litle  :confused: cuza im first time using linux  :).but no mather i like it
Here is the problem: 
I have two computers that is conected trough LAN,my brother computer is conected to internet directly.How to setup ICS on my brother computer so that i can acces internet?
And how to share some folder that hi can acces it?

---

### Post by nocturn on 2005-02-25
For the connection sharing, I recommend getting a cheap router firewall and putting both systems behind it, it is easy to do and quite secure.
If that is not an option, set up connection sharing on his system.
Set the IP address of his computer as the default gateway on yours.  I think you will also have to enter his IP as DNS server on yours.

---

### Post by nocturn on 2005-02-25
Sharing a folder to his machine is the easiest if you configure Samba on your system.

---

