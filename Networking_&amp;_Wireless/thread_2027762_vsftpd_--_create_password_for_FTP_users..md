---
title: "vsftpd -- create password for FTP users."
date: 2012-07-16
forum: Networking &amp; Wireless
---

### Post by jiapei100 on 2012-07-16
Hi, all:

Environment:
Ubuntu 12.04


I'm trying to create a server on the local computer using vsftpd.
I believe I followed the steps described [http://cviorel.easyblog.ro/2009/03/05/how-to-setup-vsftpd-ftp-on-ubuntu-linux/]("http://cviorel.easyblog.ro/2009/03/05/how-to-setup-vsftpd-ftp-on-ubuntu-linux/")

However, when I tried to login, it seems the **password** of the **ftpuser** I specified is not set. I'm wondering if it's possible for vsftpd to tell: the desktop login user and FTP user? IMO, these 2 users should/might be different, right? So, how to set the **password** specifically for the FTP user, without entangling with the desktop users??


Cheers
Pei

---

### Post by Sergius14 on 2012-07-17
On Linux there is no easy way out to do that...


FTP Users are in fact local "desktop" users.


There are some weird implementations to use users created in a Database but, to answer your question, it is not that easy as a FileZilla FTP Server (with their own users, acl's, etc.).


Linux FTP Servers variants are more likelly IIS FTP Server.

FileZilla Server it really rocks but unfortunatelly it is not compatible with linux and impossible to port.

---

### Post by jiapei100 on 2012-07-17
Hi, Thanks for your prompt reply, Sergius.

BTW, do you mean, vsftpd is the thing that FileZilla is using?
In fact, I used vsftpd to create a server,
while I was trying to connect the server through FileZilla client,
but failed...

So, any further suggestions?

Cheers
Pei

> **Sergius14 said:**
> On Linux there is no easy way out to do that...


FTP Users are in fact local "desktop" users.


There are some weird implementations to use users created in a Database but, to answer your question, it is not that easy as a FileZilla FTP Server (with their own users, acl's, etc.).


Linux FTP Servers variants are more likelly IIS FTP Server.

FileZilla Server it really rocks but unfortunatelly it is not compatible with linux and impossible to port.

---

