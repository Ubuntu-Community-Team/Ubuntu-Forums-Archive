---
title: "nfs permission problems"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by larsemil on 2008-12-20
I have always been using NFS without having any problems at all as long as i have the same userid and groupid on the users on the server and the client. But today i stumbled into a problem i have never had before - root owning all the folders after mounting. normally the permissions come along with the share.

here is something to show you what i mean:

On the client
```
#
larsemil@mamin:/mnt/server$ cat /etc/fstab
#
# /etc/fstab: static file system information.
#
#
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#
proc            /proc           proc    defaults        0       0
#
# /dev/sdc1
#
UUID=cc870487-8046-4b3b-bbac-fb5d336dd63b /               ext2    relatime,errors=remount-ro 0       1
#
 
#
#nfs mount
#
192.168.1.68:/mnt /mnt/server nfs hard,intr,users,rw    0   0
#
 
#
 
#
 
#
ls /mnt/server -l
#
larsemil@mamin:/mnt/server$ ls /mnt/server -l
#
total 20
#
drwxr-xr-x 2 root root 4096 2008-12-14 17:03 ma
#
drwxr-xr-x 2 root root 4096 2008-12-14 17:04 ma2
#
drwxr-xr-x 2 root root 4096 2008-12-20 19:31 server
#
drwxr-xr-x 2 root root 4096 2008-11-08 21:37 warez
#
drwxr-xr-x 2 root root 4096 2008-11-08 21:37 warez2
#
 
#
larsemil@mamin:/mnt/server$ id larsemil
#
uid=1000(larsemil) gid=1000(larsemil) groups=1000(larsemil),4(adm),20(dialout),24(cdrom),46(plugdev),110(lpadmin),111(sambashare),112(admin)
#
 
#
 
```

And on the server:```

#
larsemil@gandalf:/mnt$ cat /etc/exports
#
# /etc/exports: the access control list for filesystems which may be exported
#
#              to NFS clients.  See exports(5).
#
#
#
# Example for NFSv2 and NFSv3:
#
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
#
#
# Example for NFSv4:
#
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
#
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
#
#
 
#
/mnt 192.168.1.0/255.255.255.0(rw,sync,no_root_squash,no_subtree_check)
#
 
#
larsemil@gandalf:/mnt$ id larsemil
#
uid=1000(larsemil) gid=1000(larsemil) grupper=1000(larsemil),4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare)
#
 
#
larsemil@gandalf:/mnt$ ls /mnt -l
#
totalt 20
#
 
#
drwxr-xr-x  2 root     root     4096 2008-12-14 17:03 ma
#
drwxr-xr-x  2 root     root     4096 2008-12-14 17:04 ma2
#
drwxr-xr-x  7 root     root     4096 2008-12-20 19:31 server
#
drwxr-xr-x  8 larsemil larsemil 4096 2008-11-08 20:30 warez
#
drwxrwxrwx 11 larsemil larsemil 4096 2008-12-14 17:08 warez2
```


as you can se the permissions are totally different when listing the same folder from the share or locally on the server. 

and if you are interested warez and warez2 contain only linuxdists. :)

---

### Post by larsemil on 2008-12-21
bump

---

### Post by larsemil on 2008-12-23
As noone seems to know and i dont get it to work i will file a bug

---

