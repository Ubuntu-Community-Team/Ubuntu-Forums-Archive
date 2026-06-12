---
title: "vsftp user/folder setup?"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by IceQube on 2009-12-12
Hello. I have recently installed ubuntu server on my new Power Mac G4 server, but i am having problems setting my vsftp server up correctly. What i want is two users. one who can upload and download, and create/delete directories. and another user who can just download. thats kinda easy. but here comes the part i am having trouble with.
lets say that the user with read/write permission has his ftproot in /srv/ftp. what i then want is a folder inside that (/srv/ftp/guest) that will be the other users ftproot. so if i login with the first user with read/write permissions, i can upload files to both /srv/ftp and /srv/ftp/guest. the when i lgo in with the other user i can download files from /srv/ftp/guest.

Can anyone help me with setting up the users, permissions and vsftp configuration?

regards, Adam Honoré.

---

### Post by Lars Noodén on 2009-12-12
If you are interested in having secure connections then you will want to use SFTP instead of FTP or FTPS.  

openssh-server has a built-in sftp support. That will give you an encrypted way to transfer files easily. SFTP is a new protocol, not FTP over SSL. From a user perspective, it works like FTP with nice clients like filezilla, konqueror, dolphin, nautilus, cyberduck, or fugu.

For the second user to have read-only access to those directories, don't add them to any groups that have write access to those directories.

---

### Post by IceQube on 2009-12-12
It has to be ftp. because the guests doesent have to use a special client.

---

### Post by Lars Noodén on 2009-12-13
> **IceQube said:**
> It has to be ftp. because the guests doesent have to use a special client.

FTP does have a few more clients available.  However, if your users are using Fetch or Filezilla, then they already have sftp support.  

The file managers dolphin, thunar and nautilus also support sftp.  
So does Konqueror.  Firefox, Opera, and Epiphany lack sftp support.

---

