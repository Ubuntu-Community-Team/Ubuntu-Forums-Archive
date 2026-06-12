---
title: "FTP and /var/www"
date: 2012-04-03
forum: Networking &amp; Wireless
---

### Post by robmoss2k on 2012-04-03
I'm having some major problems trying to share out /var/www via FTP. Before you start saying I should use SFTP, FTPS or similar - don't bother - this is for communication with a SAP system and it has no support for those protocols, and installation of third party tools on the operating system violates the support contract, so it's FTP or nothing.

I've tried vsftpd, proftpd and now pure-ftpd. All of them have the same problem - no matter what I do, I don't seem to be able to write files. Anywhere. No matter whether I'm using anonymous access, pure-ftpd users, proftpd users, vsftpd users, local system users, root, whatever - nothing will give me anything other than:

STOR error.jpg
550 Access is denied.

As you can imagine, this is really quite frustrating. I followed the instructions here to set up my FTP server, minus the bit about pureadmin as I don't want X Windows:

[https://help.ubuntu.com/community/PureFTP](https://help.ubuntu.com/community/PureFTP)

Now it's become slightly worse - I can log in, but I can't even list the contents of my own home directory.

So before I go mad, can someone please explain to me how I set up an FTP server (any will do - I don't care as long as it's old-fashioned insecure FTP) which will chroot some user in /var/www, allow file uploads, downloads and overwrites, chown the files that get uploaded to www-data:www-data and chmod them to 775.

Many thanks in advance to anyone who can help!

---

### Post by yanom on 2012-04-22
*bump* having the same problem here....
anyone...

---

