---
title: "Can't see shared folder on the network"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by rudlavibizon on 2009-10-28
I have three machines connected via a router: Ubuntu desktop (9.10rc), Ubuntu netbook with UNR (9.10rc) and WinXP desktop. The netbook is connected by wireless and the other two by wired connection. The desktop machine can "see" WinXP and vice-versa using samba and nautilus sharing, no problems there, but the Desktop can't see Netbook's shared folders. I tried sharing with gksudo nautilus to no avail, installed smbfs, changed a smb.conf entry to browsable = yes, I even copied the smb.conf from Desktop to netbook. Both computers were updated yesterday.

Of course the question is can anyone help me out with this baffling problem?

Thanx

PS. Not sure if that may have something to do with this but I have the same username and password on both Desktop and Netbook.

---

### Post by rudlavibizon on 2009-10-28
I've found out what it is. The samba deamon is not loaded at startup for some reason. How do I set it to start?

---

### Post by Iowan on 2009-10-28
If it were Jaunty, I'd suggest looking in System>Preferences>Startup Applications. (The note says these start when you log in.)

---

### Post by rudlavibizon on 2009-10-28
I don't think it would work since you need to have root privileges. Anyway I found out that it's a bug that affects other people too. The nmbd daemon exits because it's started before the IP address is assigned. The bug is confirmed in launchpad and has the high priority so hopefully it will be fixed soon. Here is the launchpad page:

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/462169](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/462169)

---

