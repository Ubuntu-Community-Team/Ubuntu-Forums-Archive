---
title: "vsFTPd starting up problem"
date: 2012-08-30
forum: Networking &amp; Wireless
---

### Post by manny6574 on 2012-08-30
Hello, I am new to Ubuntu, and very new to any type of server tech. 

Last night I was setting up a server with Ubuntu Server 12, I wanted to set up an FTP server. I looked around and found that vsftpd is a fine solution so I installed it, changed a couple settings  in the vsftpd.conf file. I noticed that I could connect very well if a user on the server was logged in and started the service, but if one was NOT logged in I could not establish a connection. 

I google around already, and did a lot of the stuff but it didn't work.

Any ideas on how to start it up automatically? I really would like to get it set up soon.. :(

---

### Post by Lars Noodén on 2012-08-30
If all you want to do is transfer files securely and are not wed specifically to FTP, then you could use SFTP instead.  It's part of the package [openssh-server](apt://openssh-server) and needs no further configuration for basic usage.  Odds are you already have the ssh server installed so there is nothing extra you need and you could safely uninstall the FTP service, it being just one more thing to worry about otherwise.

There are, of course, use cases where FTP is valid, but for the most part it is time to consign it to history:

[list]
[*] [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)
[*] [http://www.openlogic.com/wazi/bid/188103/](http://www.openlogic.com/wazi/bid/188103/)
[/list]

There are SFTP clients built into Nautilus, Dolphin and others.

---

### Post by manny6574 on 2012-08-30
Thanks, works now with openssh ;)

---

