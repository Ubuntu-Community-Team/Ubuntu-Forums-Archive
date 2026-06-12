---
title: "Samba connection issues"
date: 2013-05-08
forum: Networking &amp; Wireless
---

### Post by carboi82 on 2013-05-08
Recently I have found myself unable to access samba shares on an ubuntu machine on anythign except through port 22 (sftp) using filezilla, or simply through windows explorer from a windows machine. Since it's for accessing a media server, and sending ~30gb blu-ray rips (totally legal), speed is obviously preferred. Sending over an sftp connection is significantly slower than it was with just a standard ftp connection, and the cut/paste function from windows has a decent overhead which knocks down the transfer speed as well.

Anyone know why ubuntu would allow the sftp connection on port 22, but reject the ftp connection on port 21 with the same credentials?

---

### Post by Beast12 on 2013-05-10
Did you checked your UFW settings?

---

### Post by carboi82 on 2013-05-10
Its my understanding that ufw is disabled by default, and has never been turned on by me (and after double-checking, is still inactive). 
Also, since it allows a non-credentialed connection from windows it seems odd that ufw would allow that and not an ftp connection. Good suggestion though :D

---

### Post by bab1 on 2013-05-10
> **carboi82 said:**
> Recently I have found myself unable to access samba shares on an ubuntu machine on anythign except through port 22 (sftp) using filezilla, or simply through windows explorer from a windows machine. Since it's for accessing a media server, and sending ~30gb blu-ray rips (totally legal), speed is obviously preferred. Sending over an sftp connection is significantly slower than it was with just a standard ftp connection, and the cut/paste function from windows has a decent overhead which knocks down the transfer speed as well.

Anyone know why ubuntu would allow the sftp connection on port 22, but reject the ftp connection on port 21 with the same credentials?

The sftp protocol is really SSH.  The TCP port 22 is for SSH (ssh scp and sftp).  No FTP server is used at all with sFTP.  The default Ubuntu install does not include an FTP server, so you should not be able to connect on TCP port 21.  

The protocol defines which port the application uses.  It sounds like this is not a credentials issue at all.  If you insist on using FTP then you have to install the server to use it.

I'm almost afraid to ask; What do you mean by this?> ...I have found myself unable to access samba shares on an ubuntu machine on anythign except through port 22 (sftp) using filezilla, or simply through windows explorer from a windows machine.

Can you browse shares?  Can you mount the shares via the *network *icon?

---

### Post by carboi82 on 2013-05-10
> **bab1 said:**
> Can you browse shares?  Can you mount the shares via the *network *icon?

Yes, I can mount/browse/create/delete/etc from windows explorer. 

You, sir or ma'am, are now my favorite person of the day though. I apparently forgot to reinstall an ftp daemon the last time I rebuilt the system. Amazing how its possible to overlook the simplest things sometimes...

---

