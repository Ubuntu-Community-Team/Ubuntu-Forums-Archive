---
title: "Friendly NFS Share Names"
date: 2013-01-07
forum: Networking &amp; Wireless
---

### Post by wt9bind on 2013-01-07
Hi,

I am running Ubuntu as a media server and access my NFS shares via my WD HD TV Live and Mac.

I am hoping somebody could tell me how I give my shares friendly names.

Right now they are off of the volume names given automatically to my Hard Drives from Ubuntu

The only one with a friendly name are my kids cartoons and I have no idea how I did this now :rolleyes:

My exports looks like this:

```

# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/export/sdd1    192.168.1.0/255.255.255.0(rw,sync,all_squash,insecure,anonuid=1000,anongid=1000,no_subtree_check)
/export/deluge  192.168.1.0/255.255.255.0(rw,sync,all_squash,insecure,anonuid=1000,anongid=1000,no_subtree_check)
/export/sdb1 192.168.1.0/255.255.255.0(rw,sync,all_squash,insecure,anonuid=1000,anongid=1000,no_subtree_check)
/export/sdc1 192.168.1.0/255.255.255.0(rw,sync,all_squash,insecure,anonuid=1000,anongid=1000,no_subtree_check)
/export/Kids/kids 192.168.1.0/255.255.255.0(rw,sync,all_squash,insecure,anonuid=1000,anongid=1000,no_subtree_check)
/export/Kids 192.168.1.0/255.255.255.0(rw,sync,all_squash,insecure,anonuid=1000,anongid=1000,no_subtree_check)
/home/FTP-shared/upload/export 192.168.1.0/255.255.255.0(rw,sync,all_squash,insecure,anonuid=1000,anongid=1000,no_subtree_check)
/home/FTP-shared/upload 192.168.1.0/255.255.255.0(rw,sync,all_squash,insecure,anonuid=1000,anongid=1000,no_subtree_check)
/media/sdd2     192.168.1.0/255.255.255.0(rw,sync,all_squash,insecure,anonuid=1000,anongid=1000,no_subtree_check)


```

Attached is how it looks in Mac.



What I would like is if:
 SDB1 was called TV
SDC1 was called Movies
SDD1 was called Music
SDD2 was called Documentaries

Can anybody advise how I could do this?

Thanks in advance

---

### Post by LewisTM on 2013-01-08
I'd be curious to know how you mounted these drives and what made you decide to use that export structure. Are the drives in /export bind mounts? What does your /etc/fstab file contain? This is the place where you determine how, where and under what name to mount the volumes at boot time.

Cheers!

---

### Post by wt9bind on 2013-01-08
Fstab looks like this:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda1 during installation
UUID=8d27da22-6f0e-4c4b-8385-c800c579982e  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda5 during installation
UUID=386df752-390c-4c51-9d7f-7089fa147993  none         swap  sw                   0  0  
/dev/sdb1                                  /media/sdb1  ext4  users,user,owner     0  0  
/dev/sdc1                                  /media/sdc1  ext4  users,user,owner     0  0  
/dev/sdd1                                  /media/sdd1  ext4  users,user,owner     0  0  
/dev/sdd2                                  /media/sdd2  ext4  users,user,owner     0  0  
/media/sdd1  /export/sdd1  bind  bind  0  
/media/sdd2  /export/sdd2  bind  bind  0  
/home/deluge  /export/deluge  bind  bind  0  
/media/sdb1  /export/sdb1  bind  bind  0  
/media/sdc1  /export/sdc1  bind  bind  0  
# /dev/sda3
UUID=5c7c9a1e-ff5b-4258-9fd0-133fbc3f6642  /media/kids  ext4  users,user,owner     0  0  
/media/kids  /export/Kids/kids  bind  bind  0  
/export  /home/FTP-shared/upload/export  bind  bind  0  

```

---

### Post by LewisTM on 2013-01-09
The way to go should be pretty evident.
Just rename your bind mount points to something more descriptive.
```
/media/sdd1  /export/Music  bind  bind  0  
/media/sdd2  /export/Documentaries  bind  bind  0  
/home/deluge  /export/deluge  bind  bind  0  
/media/sdb1  /export/TV  bind  bind  0  
/media/sdc1  /export/Movies  bind  bind  0  
```
Of course the corresponding directories should be created under /export and the entries should be edited accordingly in your /etc/exports file.

Once this is done, you can reboot for the changes to take effect. You can then delete the empty, useless /export/sdXX directories if you wish.

---

### Post by wt9bind on 2013-01-09
Thanks Lewis. I am very new to all of this so appreciate you pointing out the obvious to me.

Cheers

---

