---
title: "Ubuntu 8.10 FTP client with Ident Server?"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by nikkyo on 2008-12-17
Hello, in windows i use FTPrush to connect to ftp's with ident server. But in ubuntu i have not found any ftp client with server ident.

I tried to use pidentd, but i dont know where to set the name of the ident and in /etc/inetd.conf i do not see much.

I want this:
[http://www.ftprush.com/ftp-ident-server.html](http://www.ftprush.com/ftp-ident-server.html)

Someone can help me?

---

### Post by Colt45 on 2008-12-27
You aren't going to find an FTP client with a built in ident server for linux.

If you need ident, you'll need to setup a separate ident server.

It will take some work, but it can be done.

---

