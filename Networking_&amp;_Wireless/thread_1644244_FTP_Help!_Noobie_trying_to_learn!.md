---
title: "FTP Help! Noobie trying to learn!"
date: 2010-12-13
forum: Networking &amp; Wireless
---

### Post by urkrnboy90 on 2010-12-13
So as the title says...I am a beginner with creating a FTP server.

I found a proftpd guide here on ubuntu forums and followed that guide to install proftpd and also configure the proftpd.conf file. I created a directory in /home/FTP-shared called "download" to put my files in there for access. I can connect to my ftp server on my computer by typing in [ftp://localhost](ftp://localhost) and typing in the correct credentials. But what I really want to be able to do is access my ftp server that I just built on my linux box from literally anywhere (school, iphone, brother's computer, etc).

Could someone guide me to the right place or instruct me on how to do so? I've been looking everywhere (even outside of ubuntuforums) to learn how to do so but I couldn't find much. 

Thanks ahead!!!!

---

### Post by karthick87 on 2010-12-13
If you want to access outside from your home then you should type **[ftp://yourftpserverip](ftp://yourftpserverip) **you should give your external ipaddress of the ftpserver.For privacy if you want to hide your ip address then you can register in [www.dyndns.com/]("http://www.dyndns.com/") Also if you have Firewall enabled in your system you should all port 21.

---

