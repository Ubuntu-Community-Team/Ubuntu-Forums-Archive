---
title: "Help With my network"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by zocrates on 2009-11-17
So, I fell in love with Ubi (that is what I call it) since 7.04.  Not being a techie I've gone a long way and have learned alot.  The one thing I have not figured out yet, and I need some help with is how to secure a specific folder in my server; let me explain myself.  i run a home server (ubu serv lts 8.04) and in this server we share EVERYTHING all over, it is GREAT and it was so easy to do, but now me and the missus have decided to put our honeymoon pictures and other "private videos" on the network so they can also benefit from the RAID and we don't loose them.  Well, some of the things we are going to put in there I would not like my kids to access and would like to either restrict the access to that folder.  It can't be too hard, nothing really is in linux I noticed, but I haven't found out how to yet.  Could someone point me in the right direction or give me a hint.


Thank you guyz LLL

---

### Post by Iowan on 2009-11-17
Are you planning to share them or just store them? Meaning, Ubuntu directories can be access-limited by adjusting permissions. If you need to access them as shares, you should still be able to control access. 
How are files currently shared - Samba, NFS, etc.?
If Samba, is **security=share**?

---

### Post by zocrates on 2009-11-18
I'm using SAMBA and I'd like to share them but limit the access to me and the wife, nobody else.  My file Server is used primarily as a huge shared drive in my home, downloads in one computer are available to all is the philosophy here at the house

---

### Post by Iowan on 2009-11-18
How is security set up (in */etc/samba/smb.conf*)? Is it **security=share ** or **security=user**? (Or maybe something different.) You can set a **valid users =** parameter for a share.

---

### Post by zocrates on 2009-11-19
it's set up as Share

---

### Post by Iowan on 2009-11-19
Dunno if the **valid users =** parameter overrides **security=share**. I suppose you could set up a test share and make yourself a valid user - then try to log on as someone else. (or set up with someone else as the valid user, then see if you can access it. **sudo** should still let you modify things.

---

### Post by zocrates on 2009-11-20
Thanks, i'll give it a shot.  just for the record i am one of those "thanx to Ubuntu" Linux users, still have the GUI thumb in my mouth, but little by little am learning to walk the swing step of linux.  jeje

---

### Post by Iowan on 2009-11-20
Before you know it, you'll be using regular expressions in shell scripts... :D

---

