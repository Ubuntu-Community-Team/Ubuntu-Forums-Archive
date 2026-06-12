---
title: "LUFS and fstab"
date: 2006-01-26
forum: Networking &amp; Wireless
---

### Post by polt on 2006-01-26
Does anybody know how to make a correct entry for LUFS in fstab?  I tried the following:

none  /mnt/mountpoint  lufs nosuid,fs=ftpfs,host=ftp.mysite.org,username=xxx,password=yyy,ftpactive	0	0

My FTP fails to mount on startup.  However, if I type "mount -a", that seems to work okay.

---

### Post by polt on 2006-01-28
There is also an error on shutdown if i do the mount -a command, which doesn't appear if i do not do the command.  Doesn't anyone know anything about mounting ftp servers?  should i use FUSE instead of LUFS perhaps?

---

### Post by polt on 2006-01-31
Okay, i found some more info. on this problem.  When I mount my ftp file system and try to copy files onto it, I get this error

"There is not enough space on the destination."

Which is weird, because if I go to the ftp address using the program "ftp", I have no problem copying files there.  So there is obviously enough space on the destination.:cry:

---

