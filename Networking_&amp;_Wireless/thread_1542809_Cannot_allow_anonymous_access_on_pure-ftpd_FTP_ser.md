---
title: "Cannot allow anonymous access on pure-ftpd FTP server"
date: 2010-07-31
forum: Networking &amp; Wireless
---

### Post by csh on 2010-07-31
I installed Ubuntu Server 10.04 in VirtualBox together with LAMP server.

Then, I installed Pure-FTPd FTP server.

I had done the following.

1. Created a directory 'myftpfiles' in /var/www.
2. Created a group name and a user name 'ftp', with the home directory set to /var/www/myftpfiles.
3. The permission of /var/www/myftpfiles to 775.
4. The file /etc/pure-ftpd/conf/NoAnonymous has been set to 'no'.
5. Restart the FTP server by using the command "sudo /etc/init.d/pure-ftpd restart".

But, when I try to access the FTP site from Windows host with Firefox, I am still prompted to enter user name and password. Why?

---

