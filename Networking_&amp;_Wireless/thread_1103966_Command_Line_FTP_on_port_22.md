---
title: "Command Line FTP on port 22?"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by CarlosinFL on 2009-03-23
I am trying to ftp using the CLI and the ftp server is using port 22 (SFTP) rather than 21. How can I force the CLI to connect to a FTP URL using port 22 rather than the default?

I tried doing the following:

```
cwilliams@tunafish:~$ ftp
ftp> open ftp.blahblahblah.com:22
ftp: ftp.blahblahblah.com:22: Unknown host
```

---

### Post by Bachstelze on 2009-03-23
SFTP and FTP are totally different protocols. You can't connect to a SFTP server using a FTP-only client. To connect to a SFTP server from the command-line, do

```
sftp user@host
```

A list of SFTP commands is available [here]("http://kb.iu.edu/data/akqg.html").

---

### Post by thehouseofho on 2009-03-23
You should be using the command 'sftp' to connect to an SFTP server.

---

### Post by CarlosinFL on 2009-03-23
Thanks so much. I knew it was something easy I was missing ;)

---

### Post by apmcd47 on 2009-03-23
> **Carlwill said:**
> I am trying to ftp using the CLI and the ftp server is using port 22 (SFTP) rather than 21. How can I force the CLI to connect to a FTP URL using port 22 rather than the default?


Try a different FTP client? My current favourite is lftp:
```
lftp -u user sftp://host/dir/hier/
```
If you do, eg **[ftp://host/dir/hier:22](ftp://host/dir/hier:22)** it will assume FTP protocols at port 22, rather than use SFTP protocols.

lftp can be used for ftp, sftp, fish, http and possibly others.

Andrew

---

