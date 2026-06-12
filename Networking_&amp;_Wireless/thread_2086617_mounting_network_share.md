---
title: "mounting network share"
date: 2012-11-21
forum: Networking &amp; Wireless
---

### Post by dwlamb on 2012-11-21
I am using this [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently) article to set-up a  share on my machine.

If I attempt to mount using sudo mount -a I receive an error of

mount error: could not resolve address for xp2: Unknown error

This happens if I attempt with the credentials directly in the fstab line or using a file to hold the Windows username and password.

If I use the IP of XP2 in the fstab, I get the following message if I attempt to mount

mount error(13): Permission denied

yet, if I do smbclient -L XP2 -Udaniel I get a listing of all the shares under XP2. Same if I use XP2's IP address.  This is My fstab entry:
```

//xp2/backup /media/xp2_backup cifs credentials=/home/daniel/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```Is there a step missing?

---

### Post by 2F4U on 2012-11-21
Have you tried writing xp2 in upper case letters or use the IP address in /etc/fstab?

---

### Post by dwlamb on 2012-11-21
I meant to add that information.... Yes, I have tried upper and lower case.

> **2F4U said:**
> Have you tried writing xp2 in upper case letters or use the IP address in /etc/fstab?

---

### Post by dwlamb on 2012-11-26
Doing some further research on this, I came up with [this blog]("http://vijayk.blogspot.ca/2008/09/cifs-mount-error-13-permission-denied.html").  It is old but the method provided and cited below works.  
```

$[FONT=monospace]mount -t cifs //win-share-hostname/share /mnt/win -o username=user,password=passwd,domain=xxx[/FONT]
```Using this method, the mount point is under /media not /mnt.

I don't know what it is.  I used the same guide cited in my original post to try ad set-up permanent shares under Ubuntu 10.04 and could not get it to function using the fstab method.  I'd still like a permanent solution.

---

