---
title: "Disks not showing in nfs mount"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by dmizer on 2009-05-20
On the NFS server, I have two internal hard drives mounted inside /home/dmizer/media, the fstab lines look like this:
```
UUID=516432aa-9173-4ef2-8d0e-9784640281ff /home/dmizer/media/Music   ext3    relatime,errors=remount-ro 0       1
UUID=edace5ef-56c0-4446-9243-795a0a0e3992 /home/dmizer/media/Movies  ext3    relatime,errors=remount-ro 0       1
```
Permissions look like this:
```
$ ls -l /home/dmizer/media/
drwxrwxrwx  90 dmizer dmizer 4096 May 21 09:21 Movies
drwxrwxrwx 154 dmizer dmizer 4096 May 21 09:19 Music
```
Here's the /etc/exports line:
```
/home/dmizer/media      192.168.24.0/24(rw,no_root_squash,async,no_subtree_check)
```

Now, for the client, I have this line in /etc/fstab:
```
192.168.24.51:/home/dmizer/media /media/server-media nfs rsize=8192,wsize=8192,timeo=14,intr
```
I can see the Music and Movies folders in the mounted directory:
```
$ ls -l /media/server-media/
total 8
drwxr-xr-x 2 dmizer dmizer 4096 May 20 17:19 Movies
drwxr-xr-x 2 dmizer dmizer 4096 May 20 17:20 Music
```
But I can't see any of the files in either Media or Music:
```
$ ls -la /media/server-media/Music/
total 8
drwxr-xr-x 2 dmizer dmizer 4096 May 20 17:20 .
drwxrwxrwx 4 dmizer dmizer 4096 May 20 17:20 ..
```

If I export either /home/dmizer/media/Movies or /home/dmizer/media/Music separately, I can mount mount and display the contents with no problem. Is this a limitation of NFS, or am I doing something wrong?

---

### Post by dmizer on 2009-05-21
Finally found my answer here: [http://doxfer.com/Webmin/NFSExports#Exporting_a_directory](http://doxfer.com/Webmin/NFSExports#Exporting_a_directory)

> Only directories on local filesystems can be exported via NFS, so it is not possible to re-export files that have been mounted from another NFS server. Neither is it possible to export directories from non-Unix filesystems such as vfat, ntfs or iso-9660. If an exported directory has mount points under it, files under those mount points will not be accessible by NFS clients. So if you exported the root directory / and has a separate filesystem mounted at /home , you would need to also export /home and clients would need to mount it in order to see the files under it.

:(

---

