---
title: "Problem mounting windows share in fstab"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by Colci on 2010-03-07
I want to access one directory and two drives on a windows xp machine on the home network. So I read a lot and altered by fstab as follows

```
//xpcomputer/XPCMusic /media/netstorage/XPCMusic cifs         credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0  0

//xpcomputer/Softlib /media/netstorage/softlib cifs             credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777  0  0  

//xpcomputer/XPCPhotos /media/netstorage/XPChotos cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777  0  0  
```

No problem with the photos directory, I can get into that a see everything that is on the drive,  even in sub-directories.  On the softlib I cannot see anything whereas on the Music drive I can see a list of all the top level directories but no more. As far as I can see all permissions etc, on the xp computer are identical.  Any idea what I might be doing wrong?

---

### Post by cjhabs on 2010-03-07
> **Colci said:**
> I want to access one directory and two drives on a windows xp machine on the home network. So I read a lot and altered by fstab as follows

```
//xpcomputer/XPCMusic /media/netstorage/XPCMusic cifs         credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0  0

//xpcomputer/Softlib /media/netstorage/softlib cifs             credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777  0  0  

//xpcomputer/XPCPhotos /media/netstorage/XPChotos cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777  0  0  
```

No problem with the photos directory, I can get into that a see everything that is on the drive,  even in sub-directories.  On the softlib I cannot see anything whereas on the Music drive I can see a list of all the top level directories but no more. As far as I can see all permissions etc, on the xp computer are identical.  Any idea what I might be doing wrong?

Maybe it is the share permissions of the folders on the XP box.

---

### Post by Colci on 2010-03-08
> **cjhabs said:**
> Maybe it is the share permissions of the folders on the XP box.

Thanks but no the permissions are the same on the XP computer.  If I connect via nautilus via "connect to server"  & "windows shares" I can browse these drives, the directories and sub-directories and read the files.  Everything seems identical and I cannot understand why the photos drive  is fully accessable but the other two not.

---

