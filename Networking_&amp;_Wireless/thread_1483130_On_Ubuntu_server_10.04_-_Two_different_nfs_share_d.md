---
title: "On Ubuntu server 10.04 - Two different nfs share display same content"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by aigore on 2010-05-14
Hello everybody, I'm configuring an ubuntu server on 10.04.
This server is for dhcp and sharing purposes.
I can actually access one nfs share via other ubuntu and osx clients on the network, then I configured another share with different mount point (different drive, different forlder, different contents).
The problem is: when I connect form a client to the new one it displays the same exact content of the first share. 
It seems that is mounting the same share on a different mount point on the client and exporting the shares via the exportfs -ra command doesn't solve nothing.

This is my fstab file
```

proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=175c187c-0475-4fe8-a6d7-b0db3a423d58 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=76fc438c-8659-4513-9a53-79f1125ea700 none            swap    sw              0       0

/dev/sdb5       /mnt/archivio   ext4    rw,noatime,user 0       1
/dev/sdc5       /mnt/backup     ext4    rw,noatime,user 0       1
/mnt/archivio   /mnt/nfs/archivio       bind    bind    0       0
#/mnt/backup    /mnt/nfs/backup         none    bind    0       0     

```

And my /etc/exports
```

/mnt/nfs/archivio       192.168.0.0/255.255.255.0(sync,insecure,no_subtree_check,rw,fsid=0)
/mnt/backup     192.168.0.0/255.255.255.0(sync,insecure,no_subtree_check,rw,fsid=0)


```

Actually the last entry in fstab is commented because I was trying to bind the folders to other different mount points for exporting nfs from these, but it didn't worked...

Please help me, I'm going mad.....:confused:
Thank you all!!

---

### Post by aigore on 2010-05-17
Any clue?.....Please?

---

### Post by skitmds on 2012-10-16
Did you ever find an answer to this?

---

