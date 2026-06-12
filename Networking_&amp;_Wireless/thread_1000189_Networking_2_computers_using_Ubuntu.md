---
title: "Networking 2 computers using Ubuntu"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by feelinggood on 2008-12-02
Here is my problem, I have 3 computers, 2 of them have Ubuntu 8.04 and 1 has Windows XP.  I have an external hard drive connected to my Desktop downstairs that has Ubuntu on it.  I do most of my work upstairs on the laptop using Ubuntu.  Both computers are tied in through a router, no need for wireless as of yet.  How can I view my computer downstairs, especially the external hard drive from the laptop upstairs.  Under Network I can see my other desktop that has Windows Xp on it.  Any help would be great.  The router is a linksys.  Steve

---

### Post by capitalistpiglet on 2008-12-02
If you want to share the files on the drive you have two main options, samba and nfs.
If you want the windows machine to also see the shares then samba is probably your best bet. Although nfs is easier to configure but it is not usable on windows. There is a samba howto here.
[http://ubuntuforums.org/showthread.php?t=575214]("http://ubuntuforums.org/showthread.php?t=575214")

---

