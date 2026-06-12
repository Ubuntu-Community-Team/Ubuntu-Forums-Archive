---
title: "Troubleshooting nfs performance"
date: 2010-07-20
forum: Networking &amp; Wireless
---

### Post by zorglubx on 2010-07-20
Helloes

I am running some ubuntu servers (5-7) and are using nfs quite a lot. 

My setup are this..:
Readynas nvx nas box. with nfs shares.
Full Gigabit network.

vmware box (new and quite powerful) running the servers on internal data-stores, and nfs data-store mounted from the nas via separate network interface for data storage.

The other network from the readynas is in our switched network, that our vm's can see.

The problem is this. :)

The internal mounted datastore (shown below), that is also mounted via nfs through the esxi can perform steadily with about 32MB/s write. (5GB file, so the buffer is not enough (1GB))

/dev/sdc1       /media/backup   ext3    defaults                0       2

When using the nfs mounted drive (it ends up on same volume on the readynas box), i get a performance of around 13MB/s. it is mounted like this in fstab:

xx.xx.xx.xx:/c/media /media/data/stor1/ftp nfs defaults 0    0

To check my stats, i used nfsstat and got:

jc@Idun:/etc$ nfsstat -rc
Client rpc stats:
calls      retrans    authrefrsh
1799320    0          0

So that looks nice.. i know i transferred at least 150GB since last reboot.

The mount specifics are as follows:

jc@Idun:/etc$ nfsstat -m
/media/data/stor1/ftp from xx.xx.xx.xx:/c/media
 Flags: rw,vers=3,rsize=131072,wsize=131072,namlen=255,hard,nointr,proto=tcp,timeo=600,retrans=2,sec=sys,mountaddr=xx.xx.xx.xx,mountvers=3,mountproto=tcp,addr=xx.xx.xx.xx

It looks like the rpc service is using 1 full core of cpu while transferring, but can that really be right?

If you need more data to tell whats going on, let me know.

---

### Post by zorglubx on 2010-10-07
Bump

Just wondering if there is a secret about nfs I am not aware of.

---

