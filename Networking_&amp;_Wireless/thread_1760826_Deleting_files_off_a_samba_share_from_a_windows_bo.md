---
title: "Deleting files off a samba share from a windows box"
date: 2011-05-17
forum: Networking &amp; Wireless
---

### Post by bakreule on 2011-05-17
Hello all,

I'm trying to make my music directory, located on my Ubuntu box, available to all the windows clients (Windows 7, to be specific) located around the apartment. It seems to work fine, I can see and read from the shares from my windows box, but deleting files doesn't work, I just get a permission denied.

I've tried being as lenient as I can in the smb.conf, as well as setting 777 on the affected files, nothing changes. I've read, from my various googling, that the octal file permissions aren't as important as the samba permissions. Okay fine, but how do I tell samba to ignore permissions and let everyone delete files? I've read that samba works with samba users, but again, I don't care about users, I just want a global share that anyone can connect to and read (and delete) files.

Here's my smb.conf file: [http://www.kreulen.net/smb.conf](http://www.kreulen.net/smb.conf)

As you can see, I've played around a bit with options, but I just can't seem to get anything to work.

Any help would be appreciated, thanks!

---

### Post by bakreule on 2011-05-18
bump

---

### Post by Morbius1 on 2011-05-18
As a side point, I don't know where you read this but it's incorrect:
> I've read, from my various googling, that the octal file permissions  aren't as important as the samba permissions. Okay fine, but how do I  tell samba to ignore permissions and let everyone delete files?Nothing overrides Linux file permissions. Samba can match or take away permissions as far as the remote user is concerned but it can't add permissions.

We need to take a look at the permissions of the shared directory and it's contents:
```
ls -al /mnt/mp3
```If you have many files just post the top 10 lines or so of the output.

---

### Post by bakreule on 2011-05-19
Hey, thanks for the reply... 

Here's the permissions:
drwxrwxrwx  4 root   users     4096 2007-04-21 12:04 113
drwxrwxrwx 12 root   users     4096 2004-05-19 23:37 2pac
drwxrwxrwx  3 root   users     4096 2003-08-25 20:44 311
drwxrwxrwx  4 root   users     4096 2005-07-31 10:04 50Cent
drwxrwxrwx  4 root   users     4096 2010-10-25 12:06 Aerosmith
drwxrwxrwx  6 root   users     4096 2004-09-11 17:23 Alanis Morissette
drwxrwsrwx  3 briank users     4096 2006-08-15 15:07 Alex Ubago


For the record, briank is part of the "users" group. If you descend into a directory, all the files are 777....

It would seem to me that all the permissions are there for samba to let me delete files... yet I can't... :(

---

### Post by bakreule on 2011-05-19
Well, it would seem that I've stumbled on the solution. My windows user was called brian, and my ubuntu user is briank. I had to reinstall my windows pc after a driver screwup, and I made the user briank. 

For some reason, Samba seemed to prefer this, and I can now delete files off the shares. When I mapped the network drives in windows, I checked "connect as a different user", and entered my ubuntu user/password. For the record, I did this before and it didn't work.

I can't really explain it, but it works and I'll put this thread as solved....

---

