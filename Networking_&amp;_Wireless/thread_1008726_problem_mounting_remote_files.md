---
title: "problem mounting remote files"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by jpaulb on 2008-12-11
I want to synchronize files on a laptop with those on the main computer, or be able to access file from either.
The has worked perfectly until the switch from Debain.

Laptop is running Ubuntu 8.10 and the desktop Ubuntu 8.04-64 server plus LTSP5 on the desktop for use with the laptop then it is at home.
both are running NFS kernel server, both have fixed ip's
Can anyone point out what I am missing.

Thanks


Desktop files
exports
/home			  192.168.0.100(rw,no_root_squash,async)
/backup			  192.168.0.100(rw,no_root_squash,async)

fstab
192.168.0.10:/home	/mnt/home	nfs	defaults	0	0


Mount  lap top from desktop
root@maple:/mnt# mount -av
.
mount: UUID=0f10a04c-80f4-48b4-af15-62c7586aab61 already mounted on /var
mount.nfs: timeout set for Thu Dec 11 21:02:44 2008
mount.nfs: text-based options: 'addr=192.168.0.10'
mount.nfs: mount to NFS server 'rpcbind' failed: RPC Error: Program not registered
mount.nfs: internal error


Laptop files
export
/home    192.168.0.10(rw,no_root,root_squash,async)

fstab
192.168.0.100:/home    /mnt/home    nfs    defaults,auto    0    0
192.168.0.100:/backup    /mnt/backup    nfs    defaults,auto    0    0

mount desktop from laptop
jpb@traveller:~$ sudo mount -av
mount: UUID=124a636b-3d4f-4216-87dc-71185089a796 already mounted on /home
.
mount.nfs: timeout set for Thu Dec 11 20:17:19 2008
mount.nfs: text-based options: 'addr=192.168.0.100'
mount.nfs: access denied by server while mounting 192.168.0.100:/home
mount.nfs: timeout set for Thu Dec 11 20:17:19 2008
mount.nfs: text-based options: 'addr=192.168.0.100'
mount.nfs: access denied by server while mounting 192.168.0.100:/backup
jpb@traveller:~$

---

