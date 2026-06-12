---
title: "nfs share problems"
date: 2008-01-03
forum: Mythbuntu
---

### Post by lime4x4 on 2008-01-03
i have nfs shares setup. nfs server gutsy box nfs client mythbuntu box
if i go to the desktop in mythbuntu and use thunar file manager and navigate to
/mnt/movies all my movies show up.
I changed the location in mythtv's front end to /mnt/movies but when i got to media library and select video's nothing shows up
Any ideas? I'm i changing the source in the right place?

---

### Post by Zafrusteria on 2008-01-03
You have two machines, server = gusty and client = myth.

On gusty (server) you need to have a directory you are going to share, say :

/movies

You tell NFS that you want to share a directory with an entry in the file /etc/exports

```
/movies myth(rw,subtree_check)
```

On myth, your client machine you create an empty directory where you are going to mount the movie directory from gusty called /movies. You said this was at 

/mnt/movies

You also need to tell myth that you want the nfs share mounted. You do this in the /etc/fstab file on myth. something like the following

```
gusty:/movies /mnt/movies nfs rsize=8192,wsize=8192,timeo=14,intr
```

If you move either end you must change the configuration files and tell the machine to reread the files (restart the daemon or remount the directory)

On gusty the server

```
sudo /etc/init.d/nfs-kernel-server restart

sudo exportfs -a

```

and on the client 

```
sudo mount -a
```

hope that helps.

---

### Post by lime4x4 on 2008-01-03
Thanks but i did all that already. My problem is there not showing up under mythtv but they do show up under thunar file manager

---

