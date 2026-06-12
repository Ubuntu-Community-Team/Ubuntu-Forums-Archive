---
title: "Mounting ftps with curlftpfs"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by Fredrich2k on 2008-12-13
Hi.

> me@laptop:~$ sudo curlftpfs -o ssl [ftp://username:password@url:port](ftp://username:password@url:port) mount-point
[sudo] password for me: 
Error connecting to ftp: server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt


How can I get curlftpfs to accept the certificate? Or how can I download a FTP SSL certificate and use it here?

---

### Post by jrogde on 2009-01-09
I am looking for an answer to the same issue. Did you find a solution?

---

### Post by tobitious on 2009-02-03
bounce* same here, is there anyone out there that knows hows to work this?

---

### Post by tobitious on 2009-02-03
ok, one needs to copy the original certificate into the /etc/ssl/certs/ca-certificates.crt file. then the connection gets through.

---

