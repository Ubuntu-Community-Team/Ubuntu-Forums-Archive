---
title: "Export NTFS filesystem through NFS"
date: 2011-06-26
forum: Networking &amp; Wireless
---

### Post by camper365 on 2011-06-26
I am trying to set up an NFS server so that computers on the network can access the server's files.  There are two hard drives on the server, sda1, an NTFS filesystem mounted on /media/win1 and sdb1, a FAT32 filesystem mounted on /media/win2.  I can export /media/win2 fine and mount it from a client system.  However, when I run ```
exportfs -a
``` I get the error [/CODE]exportfs: Warning: /media/win1 does not support NFS export.[/CODE]
Here are the contents of my /etc/exports:
> 
/media/win1	192.168.1.100(rw,no_subtree_check,async,fsid=0)
/media/win2	192.168.1.100(rw,no_subtree_check)
/media/book	192.168.1.100(rw,no_subtree_check)

Here are the fstab entries for the drives:
> 
/dev/sda1       /media/win1     ntfs-3g rw              0       0
/dev/sdb1       /media/win2     vfat    rw              0       0


When I comment out the /media/win1 line of /etc/exports, the server runs properly except for the fact that /media/win1 is unavailable.  When it is uncommented, the server seems to work properly, but clients are unable to mount anything.  When I run ```
mount taft:/media/win2 /mnt
``` the program runs without any output forever (until I stop it with Ctrl+C).  I tried Googling this problem, but I couldn't find anything helpful.  Does anyone know how to export an NTFS filesystem over NFS?  My server is running Hardy.

---

### Post by SeijiSensei on 2011-06-26
Quick answer is that you can't.  NFS expects to find POSIX attributes in the file system it's exporting (like permissions, etc.) that NTFS doesn't have.  FAT32 doesn't have those properties, either, but it also doesn't care about ownerships, permissions, and the like, so it may be possible for the NFS server to ignore them in this case.  NTFS has security limitations that are incompatible with NFS exports.

Even re-exporting an NFS-mounted share is a complicated matter because of security restrictions.  You don't want to give someone the opportunity to avoid permissions on the file share just be exporting it a couple of times with a different set of usernames.

Is there some reason why the clients can't just mount the NTFS share directly over the network?

---

### Post by camper365 on 2011-06-26
> **SeijiSensei said:**
> 
Is there some reason why the clients can't just mount the NTFS share directly over the network?

What do you mean by mount directly?

---

### Post by SeijiSensei on 2011-06-26
If you want to export an NTFS file system, then use a Windows machine to do so.  I don't know whether you could use Samba on Linux instead, though you find might find [this thread]("http://fedoraforum.org/forum/showthread.php?t=262619") helpful.

---

### Post by nanog on 2011-08-26
Pleas stop with the disinformation. Ntfs-3g has worked perfectly well with NFS in linux for a long time. The problem with ntfs-3g is that it is not posix compliant so you need to use the  "no_root_squash" option.

I personally use ext3/4 for all of my mounted drives but I work with people who want to be able to remove the drive and plug it into some miscellaneous mac or pc (without installing drivers).

NFS v3:
**Export server**
# less /etc/exports | grep arch1
/media/arch1 137.53.XX.XXX(rw,no_root_squash,async)



**Destination server**

# less /etc/fstab | grep arch1
137.53.XX.XXX:/media/arch1 /media/arch1 nfs rsize=8192,wsize=8192,timeo=14,intr

# df -h | grep arch1
137.53.XX.XXX:/media/arch1
                      2.8T  1.1T  1.7T  40% /media/arch1

---

### Post by wesleykins on 2012-08-02
> **nanog said:**
> 
/media/arch1 137.53.XX.XXX(rw,no_root_squash,async)


This was PERFECT.

Thank you so much.

I had my nfs (on my local network) configured as:
```
/media/RAID6/Video      192.168.1.0/24(ro,**all_squash**,insecure)
```

This works great for ext3/4 exports, but does *not* work for NTFS exports.  I could see the export, but was unable to open/browse it.

This works beautifully:
```
/media/RAID6/Video      192.168.1.0/24(ro,**no_root_squash**,insecure)
```

Thanks again!

-Wes

---

### Post by smallbook on 2012-12-04
Hi there,

I managed to mount NTFS usb drives successfully on my linux client but I have some weird problems with it. On my NFS server, I mount 2 NTFS usb drives onto it and exported them as NFS drives. On my client, I tried to mount these 2 NFS filesystem but they appear as only 1. This means, let's assume content of ntfs 1 is aaa and content of ntsf 2 is bbb, even though exportfs shows the 2 different mount points but when I mount both, they appear as either aaa or bbb. If one of them is a ext3 or 4 it's fine. it's only when both are NTFS filesystems. 

Also, when I tried copying a huge file, let's say > 10GB, the nfs handle becomes stale. I can only copy small files.

Has anyone encountered this?

---

### Post by mfarith on 2012-12-09
I am having slightly different problems with NFS. I can see my mounts on the client machine but only the folders, I could not see the files.

Here's my /etc/export on the server:

```

/export 192.168.0.101(rw,fsid=0,no_root_squash,no_subtree_check,sync)
/export/mnt 192.168.0.101(rw,no_root_squash,nohide,insecure,async,subtree_check)

```

I've enable all possible options and still no avail.

BTW, my drives are former NTFS drives.

---

