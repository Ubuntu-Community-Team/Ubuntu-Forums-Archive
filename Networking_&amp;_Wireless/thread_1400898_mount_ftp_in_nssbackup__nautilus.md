---
title: "mount ftp in nssbackup / nautilus"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by tschuliaen on 2010-02-07
Hello
I'm trying to mount my NAS edmini harddisk in the config tool of nssbackup via ftp. 
So I*entered:
```
ftp://user:password@server/backup/
```

However i get this error:

```
Failed : [Errno 2] No such file or directory:
```

This does not happen when I mount the backup share in sbackup.

I guess the problem is that the my NAS gives back an error if someone wants to access the root directory / . Ftp listings however come back, as soon as a specific folder is selected, or let's say it is rather a "share"!

how would I*tell nssbackup (i think it uses fuse mount) to access not just the folder /backup but to use the share backup!

The same happens when I*try to mount the share backup using nautilus. All i get is:
```
Could not display "ftp://"
```
and it keeps asking for the password.

I also tried Connect to Server which gives me:
```
Error: The file is not a directory
Please select another viewer and try again.
```

---

