---
title: "2 nfs shares, one works one doesnt??? stumped :/"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by Guyver1 on 2011-05-02
ubuntu server 11.04 32bit

/etc/fstab:

```

/dev/sdc1    /media/sdc1    ext4    defaults   0    0
/dev/sdb1    /media/sdb1    ext4    defaults   0    0
/media/sdc1  /export/films  none    bind    0    0
/media/sdb1  /export/tv  none    bind    0    0

```

/etc/export:

```

/export/films  192.168.0.1/24(rw,fsid=0,insecure,no_sub_tree_check,async)
/export/tv  192.168.0.1/24(rw,fsid=0,insecure,no_sub_tree_check,async)

```

Workstation - Ubuntu 10.10 64 bit

/media/nfs1test    (for /export/films)
/media/nfs2test    (for /export/tv)

```

sudo mount -t nfs4 -o proto=tcp,port=2049 ubuntu:/films /media/nfs1test

```

works PERFECTLY!! watching a film from it right now.

```

sudo mount -t nfs4 -o proto=tcp,port=2049 ubuntu:/tv /media/nfs2test

```

results in:
```

mount.nfs4: mounting ubuntu:/tv failed, reason given by server:
  No such file or directory

```

I'm completely stumped as to why films works and tv doesnt as their configured identically.

Anyone got any idea's????

Cheers in advance.:confused::confused::confused::confused:

---

### Post by Guyver1 on 2011-05-02
tried creating a new export and fstab path to data instead of tv and still the same.... :/

---

### Post by Guyver1 on 2011-05-02
ok so I changed my /etc/exports to look like this:

```

/export  192.168.0.1/24(rw,fsid=0,insecure,no_sub_tree_check,async)
/export/films  192.168.0.1/24(rw,fsid=0,insecure,no_sub_tree_check,async)
/export/data  192.168.0.1/24(rw,fsid=0,insecure,no_sub_tree_check,async)

```

It now loads both the films and the data folders on my workstation when i do:

sudo mount -t nfs4 -o proto=tcp,port=2049 ubuntu:/ /mnt

but when i open the folders now they are both empty... cant see the sub folders and files ......

If i do:
sudo mount -t nfs4 -o proto=tcp,port=2049 ubuntu:/data /media/nfs2test

it mounts but when i open the mount to view the files i get the following window popup:

Could not display "/media/nfs2test".
Error:Error stating file '/media/nfs2test':Stale NFS file handle
Please select another viewer and try again

---

### Post by Guyver1 on 2011-05-02
ok i swapped the 2 lines around in /etc/exports and now my data folder is mounting fine on my workstation but films isnt..

It would appear that its only mounting the first line of my /etc/exports list

---

### Post by Guyver1 on 2011-05-02
Fixed it!!!

oh dear god the rush of elation!! :P

the problem was i was using fsid=0 in all my lines, that was the problem.

working now with exports looking like this:

```

/export 192.168.0.1/24(rw,fsid=0,insecure,no_subtree_check,async)
/export/films 192.168.0.1/24(rw,nohide,insecure,no_subtree_check,async)
/export/data 192.168.0.1/24(rw,nohide,insecure,no_subtree_check,async)

```

---

