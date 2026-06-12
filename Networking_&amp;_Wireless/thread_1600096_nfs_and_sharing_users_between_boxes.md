---
title: "nfs and sharing users between boxes"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by ajoywatkins on 2010-10-18
Ubuntu 9.10

So I have four boxes.  One has all the users on it and it is the nfs-server.  The other 3 are nfs-clients.  I need to be able to share all users between the boxes.  I have mounted the /home directory from the server onto the three clients as well as the /usr/local folder, however I am still unable to log in as anybody but the root on the clients.

I am not even sure how to search for this (I keep getting results on how to mount the home directory, and information about adding multiple users to a single box).

Can somebody point me in the right direction?

Thank you ahead of time. :)

---

### Post by SeijiSensei on 2010-10-18
Are /etc/passwd, /etc/group, and /etc/shadow the same on the clients as well as the server?  If, say, user "joe" has ID 1002 on the server, but ID 1001 on the client, Unix will consider them different users.  Either you need to replicate the password files across the clients, or use an ID mapper of some kind, or use a centralilzed authentication system like NIS or LDAP on the server.

I posted a simple bash script to replicate the password files using rsync [here](http://ubuntuforums.org/showthread.php?p=9893886&highlight=passwd#post9893886).  That entire thread might also prove helpful.

Beware of discussions that suggest you can use a "map_static" parameter to handle UID/GID mappings.  [This thread]("http://ohioloco.ubuntuforums.org/showthread.php?t=1457794") suggests that's no longer supported.

TBH, I'm not sure I answered your question, because I don't know what you mean by "log in" when you said:

> **ajoywatkins said:**
> I have mounted the /home directory from the server onto the three clients as well as the /usr/local folder, however I am still unable to log in as anybody but the root on the clients.

If you're simply mounting the server's /home as root to some client mount point (say /mnt/home) with the "no_root_squash" option in /etc/exports, then each user on the client should have permissions to all directories in /mnt/home to which her UID and GID would give her access on the server.  There isn't any logging in required, unless I'm missing something basic.

---

