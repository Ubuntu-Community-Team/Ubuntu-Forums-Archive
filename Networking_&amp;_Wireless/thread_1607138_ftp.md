---
title: "ftp"
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by su_penguin on 2010-10-27
Hello all,

I'm able to ftp into my server with Filezilla but, I'd like to set it up so that whoever ftp's into the server can only navigate within a certain directory. Right now, the default is /home/account but I can access other directories outside of this one; which is what I don't want. Is there anyway to restrict access to the other directories regardless of any ftp client used?

Thanks
Pengu

---

### Post by su_penguin on 2010-10-29
bump

---

### Post by cavalier911 on 2010-10-29
The FTP server controls everything.Setting up an FTP server is very complicated but a great learning experience about user accounts,permissions,configurations,etc..There is no generic answer to your question as it depends on the server software and it's configuration in addition to accounts of the computer running the server software and the permissions allowed as to whether a user can login,where they have read write access. 

Give detailed answers to all of the questions below maybe someone can steer you in the right direction. 

1.What ftp server software program did you install ?

2.Have you changed any of the default configurations on the ftp server program?

3.Are you allowing anonymous users with no password required?

4.How are the users connecting to the server that can navigate anywhere they want on the servers hard drive, local user with address 127.0.0.1 or another computer on your local area network?

---

