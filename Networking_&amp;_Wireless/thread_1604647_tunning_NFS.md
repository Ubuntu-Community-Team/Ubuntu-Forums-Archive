---
title: "tunning NFS"
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by terbor on 2010-10-24
Copying files over NFS using rsync with multiple machines running seems to slow the sync dramatically. More over when I watch to rsync copy I can see that one runs, then stops while the other runs and this carries on until one is done, but is very very slow while more then one is syncing!!!  

desktop1 59GB 64bit ubuntu 10.4 
desktop2 8GB 64bit ubuntu 10.4 
Server1 12GB 64bit ubuntu 9.10
Server2 22GB 64bit ubuntu 9.10

I have a 32 bit ubuntu 8.10 NAS with 250GB of space available.  The space isn't an issue, I'll have a total of about 100GB of used space on this when it finishes.

On the NAS here is the exports, they are all the same: 
```
/home/server1 192.168.0.155(rw,no_root_squash,insecure)
```

On the source comps here is the fstab:
```
192.168.0.151:/home/server1 /mnt/nas nfs  defaults,intr,noauto       0       0
```

The ability to connect isnt an issue, it doesn't timeout it will run until it is done, the issue is what looks like the connection keeps pausing.  The comp with 8GB to transfer has been running since last night despite the fact that rsync is telling me connections speeds of 5MBps.  If I ran them one at a time it would be fine, but I'd like to be able to set the backups to run over night which means one will kick off while another is running even if I stagger them.  rysnc is kicked off via cron on each server/desktop.

---

### Post by amauk on 2010-10-24
There could be a number of reasons for this

Try adding "async" to the NAS /etc/exports entries```
/home/server1 192.168.0.155(rw,[COLOR="Red"]async[/COLOR],no_root_squash,insecure)
```
From the exports man page> This option allows the NFS server to violate the NFS protocol and reply to requests before any changes made by that request have been committed to stable storage (e.g. disc drive).

Using this option usually improves performance, but at the cost that an unclean server restart (i.e. a crash) can cause data to be lost or corrupted.

Also, depending on how your NAS is setup, this may be a CPU bottleneck
If your NAS uses RAID 5 or 6, then the slowness could be caused by the CPU calculating the parity bits (which is fairly CPU intensive, and the reason RAID5/6 has slower write speeds than other setups)

---

### Post by terbor on 2010-10-24
I will add that option to the exports file.  thanks.

As for the memory and processor they look good and it is a raid 1.

from top

```
Cpu(s):  2.6%us,  1.3%sy,  0.0%ni, 76.2%id, 19.2%wa,  0.3%hi,  0.3%si,  0.0%st
```

```
root@bigBertha:~# free -m
             total       used       free     shared    buffers     cached
Mem:           992        976         15          0        216        673
-/+ buffers/cache:         86        905
Swap:          980          2        977
```

```
root@bigBertha:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sda3[0]
      268566528 blocks [1/1] [U]
```

---

### Post by terbor on 2010-10-24
also, I killed all the rsyncs going to this server.  However when I watch df I can see the data is still growing.  What can I use to see what is sending data on the nas? It has to be a LAN IP that is sending data, but I dont see how, none of them are syncing, I killed them all.

Thanks.

---

### Post by amauk on 2010-10-24
```
netstat -tp
```will show you current tcp connections

---

