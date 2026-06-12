---
title: "permission issue with cifs mount"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by reggler on 2009-11-25
Hi There,

There's two samba shares on our network that i would like to mount rw.
I have following in my fstab:
```
//10.243.249.9/ENGINEERING /mnt/ENGINEERING     cifs   user,username=eggler,password=XXX.uid=1000,gid=1000,mode=0755 0 0
//10.243.249.9/COMMON /mnt/COMMON               cifs   user,username=eggler,password=XXX,uid=1000,gid=1000,mode=0755 0 0

```
on mount -a i get the following
```
mount: block device //10.243.249.9/ENGINEERING is write-protected, mounting read-only
mount: cannot mount block device //10.243.249.9/ENGINEERING read-only  
```
weird enough only for one share tho even tho it all looks exactly similar on my side and i bet it's similar on the server side too....any clues what may be the problem?
if I execute mount -a again, it will mount but the mount point changes its permissions over to belong to root and i won't have write access..... what am i doing wrong here?
Thanks!
Ron:o

---

### Post by dmizer on 2009-11-25
Take a close look at the 2nd link in my sig. The mount commands given in my CIFS tutorial have more options that should help you with your read only problem.

---

### Post by reggler on 2009-11-26
> **dmizer said:**
> Take a close look at the 2nd link in my sig. The mount commands given in my CIFS tutorial have more options that should help you with your read only problem.

Ok Thanks, I did look at that and added following lines to my fstab:
```
//10.243.249.9/ENGINEERING      /mnt/ENGINEERING        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//10.243.249.9/COMMON           /mnt/COMMON             cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

Upon mount -a i weirdly get following:
```
reg@DufferinSt:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on //10.243.249.9/ENGINEERING,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on //10.243.249.9/COMMON,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Why would it not recognize **cifs** as a filesystem?
dmesg is saying following:
```
reg@DufferinSt:~$ dmesg | tail
[74780.423549]  CIFS VFS: No username specified
[74780.423556]  CIFS VFS: cifs_mount failed w/return code = -22

```
but my **/root/.smbcredentials** looks like this:
```
username=eggler
password=XXXX
```
which is weird... why does it say that there's no username specified...?

Thanks,
Ron

---

### Post by reggler on 2009-11-26
> **reggler said:**
> Ok Thanks, I did look at that and added following lines to my fstab:
```
//10.243.249.9/ENGINEERING      /mnt/ENGINEERING        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//10.243.249.9/COMMON           /mnt/COMMON             cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

Upon mount -a i weirdly get following:
```
reg@DufferinSt:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on //10.243.249.9/ENGINEERING,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on //10.243.249.9/COMMON,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Why would it not recognize **cifs** as a filesystem?
dmesg is saying following:
```
reg@DufferinSt:~$ dmesg | tail
[74780.423549]  CIFS VFS: No username specified
[74780.423556]  CIFS VFS: cifs_mount failed w/return code = -22

```
but my **/root/.smbcredentials** looks like this:
```
username=eggler
password=XXXX
```
which is weird... why does it say that there's no username specified...?

Thanks,
Ron

RESOLVED! I had to install the smbfs packet which came along with smb4k that i installed to do some further research. It's working now!
Thanks man!
Ron

---

