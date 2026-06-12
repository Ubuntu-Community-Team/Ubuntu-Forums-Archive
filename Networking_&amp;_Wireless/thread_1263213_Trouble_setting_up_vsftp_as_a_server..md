---
title: "Trouble setting up vsftp as a server."
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by PaulHuffman on 2009-09-10
I need to set up an FTP server to catch scans from an Imagistics Fax/Scanner because my old Solaris server that used to do this function is having problems staying up. I thought I'd just quickly set up an FTP server on my PC running Ubuntu 9.04, and I'd be in business. I followed the steps at [https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html]("https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html") and installed vsftp.  I tested that it was running by a command line ftp session from a PC running XP. It seemed to be working but needed some config tweeks to make it ready to take files from the scanner. I followed along in the docs and edited vsftpd.conf, making changes to be sure that anonymous user could upload files to a directory off my home. But when I tried it again I wasn't able to make the connection from my PC. I changed the permissions on my drop-off directory to 777, but still wouldn't work. I decided to start over, since I didn't remember all the changes I made to the vsftpd.conf file, I did an apt-get remove to remove vsftp, removed the vsftpd.conf file, then an apt-get install to reinstall it.  

This is the weird part- this time I wanted to make a copy of the conf file before I started messing with it, but it's not there!  And my XP isn't able to make a connect either. What did I not remove this time?  If I do a ps to make sure the ftp server is running, what would the process be called? 

On an unrelated note, after failing with Ubuntu, I thought I'd try getting an FTP server running on XP, but I can't seem to do anything right today.

---

