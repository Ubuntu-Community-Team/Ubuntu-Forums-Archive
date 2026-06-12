---
title: "provftpd server not working"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by konnorrigby on 2009-12-13
I install the provftp server on my ubuntu 9.10 machine and set everything up so you had to use a set user name and password

i hit aply and the activate.
but when i went to access it from my windows machine using filezilla, it said...
```

Status:    Connecting to 192.168.1.66:1001...
Status:    Connection established, waiting for welcome message...
Response:    220 Living_room_computer
Command:    USER connorrigby
Response:    331 Password required for connorrigby
Command:    PASS ********
Response:    530-Unable to set anonymous privileges.
Response:    530 Login incorrect.
Error:    Critical error
Error:    Could not connect to server

```

---

### Post by Lars Noodén on 2009-12-14
Filezilla supports SFTP, which is a secure file transfer protocol that works a little like FTP but is re-designed from the ground up to try to be secure.  

Edit->Settings->Connection->SFTP

SFTP is built into [OpenSSH-server](http://packages.ubuntu.com/karmic/openssh-server) and works out of the box.  So if you install that, you can try connecting with Filezilla securely.  It will be faster to set that up than trying to set up FTP rerofitted with SSL/TLS

---

