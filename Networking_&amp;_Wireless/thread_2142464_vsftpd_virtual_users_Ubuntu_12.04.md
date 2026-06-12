---
title: "vsftpd virtual users Ubuntu 12.04"
date: 2013-05-05
forum: Networking &amp; Wireless
---

### Post by acama on 2013-05-05
Hi all,
I'm trying to put in place a ftp server with vsftpd. I followed several times the instructions on /usr/share/doc/vsftpd/examples/VIRTUAL_USERS.
The main differences I see is that I have ubuntu 12.04, VSFTPD 2.3.5 and db5.1-util
So during the example, I had to create the user with adduser instead of useradd. Then I activated the user and remove the password (passwd -d virtual). At the end I have drwx------ 2 virtual 1024 mai 5 16:32 /home/ftpsite as in the example.
I used db5.1_load instead of db_load.
Apart that, the rest went well without any error message.
When I test (step 6), everything is fine till I enter the password. For the test, I keep everything like the example so the password is foo. I get a 530 Login incorrect.
It's may be an issue with vsftpd_login.db. But I don't know how to further investigate on it.
Any help ?
Alexandre

---

### Post by acama on 2013-05-07
I'm trying to investigate on the vsftpd_login.db, but does someone now how to read what is inside? This file has been created with DB5.1_load (using hash) and a text file as input. But when I try to read it with DB5.1_dump (but no hash parameter seems possible), the text is not like the original one (certainly crypted ?).
So I'm still blocked on implementing my sftp server as when I try to log on it seems not recognize the virtual users of the vsftpd_login.db file :-(

---

### Post by acama on 2013-05-08
So I continued to investigate and I found the problem...
In a nutshel,
1. first I eliminated the db5.1 issue. db5.1_dump -p allows to see that the users I created were correctly added.
2. looking on the pam (users management) file used by vsftpd (called vsftpd or ftp depending of pam_service_name in vsftpd.conf), the 2 lines of the example mentions .../lib/security/pamuserdb.so... but in ubuntu 12.04 this file is in /lib/i386-linux-gnu/security

Correcting that solve the problem...

After, the last vsftpd version 2.3.5 provides other issues in terms of permissions management as it is not possible de chroot to a writeable directory... but there are a lot of threads on that topic.

---

