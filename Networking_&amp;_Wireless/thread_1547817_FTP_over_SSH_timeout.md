---
title: "FTP over SSH timeout"
date: 2010-08-07
forum: Networking &amp; Wireless
---

### Post by djbushido on 2010-08-07
I'm having some problems with trying to do FTP over SSH. I know for sure that I have ssh working, if it's not very secure right now. I'm only on a home network.
Anyway, I can do the FTP when it's not on SSH, but using the tunnel is causing problems. I can connect to the server, but it times out trying to do a directory listing. I am using Filezilla on windows as the client, and proftpd as the server, on ubuntu.
To recap: I can connect to the server both using an SSH tunnel, and without. However, the directory listing times out trying to use an SSH tunnel.
Any ideas?

---

### Post by GlazedDonut on 2010-08-07
FTP can be hard to tunnel over ssh, try setting filezilla to use SFTP instead. Also, sftp is itself encrypted, so you dont need to tunnel it.

---

### Post by djbushido on 2010-08-07
How would one do this? I found an SFTP option, but I'm not sure what it does or how to do it.

---

### Post by GlazedDonut on 2010-08-07
In filezilla, go to the site manager. For host, put whatever the IP address or hostname of your server is. for Port, put whatever your SSH port is, probably 22, Server Type is SFTP - SSH File Transfer Protocol, Logon Type: Normal, and for user and password enter your username and password you would use to logon over ssh.

[[IMG]http://a.imageshack.us/img716/6025/sftp.th.png[/IMG]](http://img716.imageshack.us/i/sftp.png/)

---

### Post by djbushido on 2010-08-07
Thank you for that. For some reason I was trying to do the ftp port. I appreciate the help!

---

### Post by GlazedDonut on 2010-08-07
> **djbushido said:**
> Thank you for that. For some reason I was trying to do the ftp port. I appreciate the help!

You're welcome :D

---

