---
title: "LVM on 12.04 question"
date: 2012-08-25
forum: Mythbuntu
---

### Post by donb21 on 2012-08-25
Is there a way to get MythBuntu 12.04 to use LVM during the installation?  Or, should I do a two pass install; use a different program the do the LVM, and then run the MythBuntu install (i.e. use advanced partitioning and keep existing).

Any recommendations on what partitioning tool to use?  Maybe something that boots onto a Live-cd, then has partitioning selections (maybe...gpartd or something).  By the way, this is a test box with nothing on it, so no data loss concerns.

---

### Post by 2F4U on 2012-08-25
Typically, you would use the alternate install disk of Ubuntu and configure LVM during the installation procedure. After that, you would installthe mythbuntu meta package. There are guides available on how to get LVM on an existing installation:

[http://www.budzien.com/wiki/Wiki.jsp?page=LVM%20on%20Mythbuntu]("http://www.budzien.com/wiki/Wiki.jsp?page=LVM%20on%20Mythbuntu")
[https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall)

---

### Post by donb21 on 2012-08-25
Thanks for the tips.  I installed Ubuntu, then attempted to use the standard MythBuntu install CD; but it wants to re-partition.  I tried the MythBuntu site, but all it has is the MythBuntu control centre.  Where do I find mythbuntu meta packages?

---

### Post by 2F4U on 2012-08-26
You can install the mythbuntu-desktop package using either apt-get or the Ubuntu Software Center from your existing Ubuntu installation.

---

### Post by donb21 on 2012-08-26
Thanks again, the software center doesn't have anything for MythBuntu (only the stock mythtv packages).  Apt-get found it and ran.

zedo:-$ apt-get install mythbuntu-desktop

Backend setup ran; I'll continue with the remainder of the installation.

---

