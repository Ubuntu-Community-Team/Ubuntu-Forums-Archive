---
title: "Help with vsftpd"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by Arehexes on 2009-01-28
I'm a complete beginer at ftp servers and I've looked online and can't find a decent guide for this.  Does anyone know of a good place to learn how to use this ftp server program?

---

### Post by jonobr on 2009-01-28
Hello


Understanding what you need to do would be useful, that is ,
whats the FTP server OS, whats the ftp client OS,
AS you are interested in using  vsftpd
heres a walkthought in doing it

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html)

I would recommend you consider using rsync instead,
its a very simple and secure (ftp exhanges usernames and passwords in clear text and is easy to snoopin on ) copying tool that will allow you to copy from one machine to the other , and its very lightweight.
Heres details of rsync and ubuntu

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

However, more details are needed to know what should be setup where,


Cheers

---

