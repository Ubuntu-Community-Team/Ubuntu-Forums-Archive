---
title: "Problem installing ftp"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by rustyshakelford2 on 2010-01-20
I tried to install vsftp on my ubuntu 9.10 box, and i cant get it to work. I followed the tutorial exactly, and the ports are forwarded correctly. This is the output of filezilla when it tries to connect:



Status:	Connecting to XX.XX.XXX.XX:21...
Status:	Connection established, waiting for welcome message...
Response:	220 (vsFTPd 2.2.0)
Command:	USER nathan
Response:	331 Please specify the password.
Command:	PASS **********
Response:	230 Login successful.
Command:	OPTS UTF8 ON
Response:	200 Always in UTF8 mode.
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/home/nathan"
Command:	TYPE I
Response:	200 Switching to Binary mode.
Command:	PASV
Response:	421 Service not available, closing control connection
Command:	PORT 10,150,200,175,206,36
Error:	Disconnected from server: ECONNABORTED - Connection aborted
Error:	Failed to retrieve directory listing

---

### Post by puppywhacker on 2010-01-20
[http://slacksite.com/other/ftp.html#passive](http://slacksite.com/other/ftp.html#passive)

in passive mode a port for ftp-data higher than 1024 is randomly chosen. This port needs to go through the portforwarding as well.

---

### Post by Lars Noodén on 2010-01-20
I'm guessing this method was suggested from the Ubuntu server security manual.  It needs updating.

vsftpd or proftpd are not generally needed unless you want Anonymous FTP with read-only, public files.  

If you have openssh-server already installed, then you can use SFTP instead.  In contrast to FTP, SFTP is secure.  In contrast to FTPS, SFTP is easy to set up (zero config more or less) and more secure.  So probably it's already there.  Filezilla works well with SFTP.

---

