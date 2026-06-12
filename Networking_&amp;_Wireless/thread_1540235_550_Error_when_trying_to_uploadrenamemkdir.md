---
title: "550 Error when trying to upload/rename/mkdir"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by luisindahouse on 2010-07-27
the problem: when connected to my ftp server on my ubuntu 10.04 box, i cant upload/rename/mkdir, i get a 550 permission denied error. i have that problem with both vsftpd and proftpd, both with default install. same problem when i log in with different users.
 
i tried chmod'ing a file to 777, but even that file cant be renamed from my ftp client. weirdest thing ever!!
 
now, when I issue a LIST function from my FTP client, i get this:
 
drwxr-xr-x 11 1000 1000 4096 Jul 27 00:12 code
-rw-r--r-- 1 1000 1000 179 May 29 08:54 examples.desktop
drwxr-xr-x 4 1000 1000 4096 Jun 06 15:27 qBT_dir
 
why is there 1000 instead of my username and group? when I do a `ls -l` from SSH i see my username instead of the 1000... could that be the problem? how to fix?
 
many thanks!

---

### Post by yanom on 2012-04-22
sorry to necro post but... same problem.

---

