---
title: "cannot login via vftp"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by Miles_Prower on 2009-04-12
I set up a server recently for the purpose of learning server administration. I've set up sftp and can login and transfer files through that, but can't seem to get vsftpd to work I keep getting these errors when trying to log in (whether locally or on a networked machine)

```
(logging in with the machine's root account)
[root@localhost ~]# ftp localhost
Connected to localhost.localdomain.
220 (vsFTPd 2.0.5)
530 Please login with USER and PASS.
530 Please login with USER and PASS.
KERBEROS_V4 rejected as an authentication type
Name (localhost:root): root
530 Permission denied.
Login failed.
ftp> quit
221 Goodbye.

(logging in as 'tails', a user on the machine)
[root@localhost ~]# ftp localhost
Connected to localhost.localdomain.
220 (vsFTPd 2.0.5)
530 Please login with USER and PASS.
530 Please login with USER and PASS.
KERBEROS_V4 rejected as an authentication type
Name (localhost:root): tails
331 Please specify the password.
Password:
500 OOPS: cannot change directory:/home/tails
Login failed.
ftp> 
```



Seems to me that sftp is infinitely better than regular ftp, since it encrypts login credentials while en-route, but I know some people still use regular FTP. Is it worth the trouble to learn how to set up the old standard?

---

### Post by hyper_ch on 2009-04-12
well, I think those few peoples can easily switch to sftp. Tell them use use [www.winscp.com](www.winscp.com) or filezilla. There are other programs out there. Very likely the ftp client they use already has sftp capabilities. Hence I think it's not worth setting up vsftp - but that's just my 2 cents.

---

### Post by Miles_Prower on 2009-04-12
right on. Sftp was by far the easier of the two to set up. Gftp seems to handle it well enough, too.

---

