---
title: "smbget not transferring multiple files"
date: 2010-07-20
forum: Networking &amp; Wireless
---

### Post by leonardopsantos on 2010-07-20
I'm trying to do a fairly simple thing: download 2 files using smbget.

My server's name is bkpserver, my user is 'username', and the files are located at:

//bkpserver/backup/today/backup-today.tar.gz
and
//bkpserver/backup/yesterday/backup-yesterday.tar.gz

I checked my password is valid by using 
```
smbclient -L //bkpserver -U username
```
It prompts for my password and then lists the shares. So far so good. I'm trying to use this command line:

```
smbclient -u username smb://bkpserver/backup/today/backup-today.tar.gz smb://bkpserver/backup/yesterday/backup-yesterday.tar.gz
Password for backup at bkpserver: 
Using workgroup WORKGROUP, user username
smb://bkpserver/backup/today/backup-today.tar.gz
```

And that's it. It doesn't transfer the second file. If I try to transfer a single file2q
Any idea what I'm doing wrong ? The MAN page explicitly states that I can use several URLs on the same command line.

Thanks!

---

