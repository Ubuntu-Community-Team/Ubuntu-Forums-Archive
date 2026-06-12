---
title: "&quot;550 Requested action not taken&quot; with FTP action"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by aschwin on 2009-03-23
This week I bought an network hard drive from Iomega ( [http://go.iomega.com/section?SID=1eb74fa34c9b9b01edeaaf2f6b1f7e1cb20:4760&secid=76792](http://go.iomega.com/section?SID=1eb74fa34c9b9b01edeaaf2f6b1f7e1cb20:4760&secid=76792) ). I logged on to the admin site and created an FTP user. Then I wanted to make a connection to the hard drive, by SMB or by FTP. Both connection types are not working, I continue with FTP. When I start an FTP session I get the following result.

aschwin@aschwin-laptop:~$ ftp 192.168.0.10
Connected to 192.168.0.10.
220 NET Disk FTP Server ready.
Name (192.168.0.10:aschwin): 
331 User name okay, need password.
Password:
230 User logged in, proceed.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> get test.png
local: test.png remote: test.png
200 Command okay.
550 Requested action not taken.
ftp> mkdir aschwin
550 Requested action not taken.
ftp> get hallo/test.png
local: hallo/test.png remote: hallo/test.png
local: hallo/test.png: No such file or directory
ftp> get Desktop/test.doc
local: Desktop/test.doc remote: Desktop/test.doc
200 Command okay.
550 Requested action not taken.
ftp> 

Does anybody know what this means?

Kind regards,
Aschwin

---

### Post by Chatoyer on 2012-05-28
I had this same phenomenon, being very new to ftp also.  The 'put' command that I was using required the destination path and filename to be specified too, unlike msdos which infers a default destination filename to be like the source filename when none other is specified.

I hope it's obvious that I cannot promise . . . but perhaps this would work for you too.

---

### Post by drs305 on 2012-05-28
Thanks for participating.

It's been 3 years. 

Thread closed.

---

