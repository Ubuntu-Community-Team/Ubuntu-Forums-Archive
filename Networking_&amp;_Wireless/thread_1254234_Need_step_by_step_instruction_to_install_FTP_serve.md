---
title: "Need step by step instruction to install FTP server"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by rowebil on 2009-08-31
I need assistance installing FTP server.
I need help installing it via package manager or anything, then help if I run into issues then help to manage users.

I want to install a secure ftp server.
I think its called
A very secure ftp 

vsftpd
[http://vsftpd.beasts.org/](http://vsftpd.beasts.org/)
Can anyone help me with this?

---

### Post by jonobr on 2009-08-31
Install openssh from symaptic,

When thats done you can connect using command line from a remote linux box
using scp.
From a windows box you can use winscp to move arouind files.

From a ubuntu gui method go to places and connect to server.

All of the above is more secure then resgular ftp

---

### Post by Iowan on 2009-08-31
[Here]("https://help.ubuntu.com/9.04/serverguide/C/ftp-server.html") is a help page for **vsftp**.

---

### Post by uylug on 2009-08-31
```
sudo apt-get install vsftpd openssh-server
```

---

