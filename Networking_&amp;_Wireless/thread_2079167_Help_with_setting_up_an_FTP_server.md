---
title: "Help with setting up an FTP server"
date: 2012-11-01
forum: Networking &amp; Wireless
---

### Post by mahela007 on 2012-11-01
I'm trying to set up an FTP server for home use so that I can download files on my Linux computer to other devices over Wifi. I've read some of the tutorials on the forums and on other websites. 
I installed VSFTPD and added a user called "test" to Ubuntu. The user "test" isn't a system admin. The account type of test is "Desktop User" as shown in System -> admin -> Users and Groups
I've also made some changes to the VSFTPD conf file such as disabling anonymous loging, and enabling chroot_local_user. 

I can now log in to this ftp server using my other computer and my phone and I can download files without a problem. 
I would like to know if (a)this current configuration is "safe" and (b) if it's possible to change the 'root' directory that's accessed by the server when a local user logs in.

(I"m using UBUNTU 10.10)

---

