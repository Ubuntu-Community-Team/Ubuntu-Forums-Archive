---
title: "Ubuntu Server - SSH Tunneling - FTP"
date: 2010-08-15
forum: Networking &amp; Wireless
---

### Post by themattbeballin on 2010-08-15
Hello.

I am setting up SSH tunneling for a remote webserver... I have been able to tunnel EVERYTHING I need besides FTP..

and I can't figure out what the problem is.

This server is running Ubuntu Server 10.04 LTS and running ProFTPd, the latest version in the repos. 

In SSH tunnels, you connect to everything with localhost (127.0.0.1)...  and Webmin, VNC, and HTTP/HTTPS all works through that tunnel... I have  port 21 tunneled for FTP as well. and I get the following errors.. I  will Copy FIleZilla's output, and link the Windoze command line image.

```
Response:	257 "/home/gopeddle" is the current directory
Command:	TYPE I
Response:	200 Type set to I
Command:	PASV
Response:	227 Entering Passive Mode (127,0,0,1,237,233).
Command:	MLSD
Error:	Connection timed out
Error:	Failed to retrieve directory listing
```

Any help is possibly fixing this error, would be great. Thanks.

---

### Post by dmizer on 2010-08-16
Filezilla supports SFTP which works directly through SSH, so you don't have to tunnel anything for file transfer. Just configure Filezilla for a direct SFTP connection instead of a tunneled FTP connection.

This documentation should help you with that: [http://www.upenn.edu/computing/help/doc/ftp/filezillasftp.html](http://www.upenn.edu/computing/help/doc/ftp/filezillasftp.html)

I am not sure how you're tunneling things, but by the sound of it you're using the -D switch to send things through a socks proxy? If that's the case, FTP works through UDP instead of TCP. Proxies only support TCP connections. In any case, as I indicated above, you should be using SFTP instead of FTP anyway.

---

### Post by scorp123 on 2010-08-16
> FTP works through UDP instead of TCP

Definitely no :)

But classic old stupid + insecure FTP uses two ports: 20 + 21. Most people forget that. Hence why it's hard to work with through firewalls, e.g. FTP won't work if you only tunnel its control connection on port 21 but forget to tunnel the data connection back on port 20. And "passive mode" (= workaround, so the client will initiate the port 20 connection, and not the server) doesn't always work.

"  .... A client makes a TCP connection to the server's port 21. This connection, called the control connection, remains open for the duration of the session, with a second connection, called the data connection, opened by the server from its port 20 to a client port (specified in the negotiation dialog) as required to transfer file data.  ... "

[http://en.wikipedia.org/wiki/Ftp](http://en.wikipedia.org/wiki/Ftp)

---

### Post by themattbeballin on 2010-08-16
I did forget to mention I had port 20 tunneled through as well. 

I will look into SFTP, but being able to tunnel it through ports 20 and 21 would be nice too.

---

### Post by themattbeballin on 2010-08-16
Actually, SFTP worked beautifully! Thank you.

---

### Post by scorp123 on 2010-08-16
SFTP definitely is the way to go!! It will work beautifully on port 22 TCP just like SSH does and it does not require any crazy port-forwarding setups. Port 22 for SSH will do tip top.

---

### Post by themattbeballin on 2010-08-16
> **scorp123 said:**
> SFTP definitely is the way to go!! It will work beautifully on port 22 TCP just like SSH does and it does not require any crazy port-forwarding setups. Port 22 for SSH will do tip top.

I completely agree. I will totally set my FTP up like this from now on.

---

### Post by dmizer on 2010-08-16
Glad you're satisfied with SFTP. :)

> **scorp123 said:**
> Definitely no :)

But classic old stupid + insecure FTP uses two ports: 20 + 21. Most people forget that. Hence why it's hard to work with through firewalls, e.g. FTP won't work if you only tunnel its control connection on port 21 but forget to tunnel the data connection back on port 20. And "passive mode" (= workaround, so the client will initiate the port 20 connection, and not the server) doesn't always work.

"  .... A client makes a TCP connection to the server's port 21. This connection, called the control connection, remains open for the duration of the session, with a second connection, called the data connection, opened by the server from its port 20 to a client port (specified in the negotiation dialog) as required to transfer file data.  ... "

[http://en.wikipedia.org/wiki/Ftp](http://en.wikipedia.org/wiki/Ftp)

Ugh. I knew I should have looked it up. :(

Thanks for keeping me honest.

---

