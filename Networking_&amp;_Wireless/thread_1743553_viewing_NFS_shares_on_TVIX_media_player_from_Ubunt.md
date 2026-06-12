---
title: "viewing NFS shares on TVIX media player from Ubuntu 11.04"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by Guyver1 on 2011-04-29
My media player can see the shares and access but the shares are 'empty', I cant see the files and folders within the shares.

/etc/exports
```

 /etc/exports: the access control list for filesystems which may be exported
#        to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/media/TV    192.168.0.0/24(rw,sync,no_root_squash)
/media/FILMS    192.168.0.0/24(rw,sync,no_root_squash)

```



/etc/fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=7041d18e-922e-42e6-af2f-0e9cb4593158 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=34598a38-2fe3-4db3-8713-6e498d2af58e none            swap    sw              0       0
/media/TV	/export/tv	none	bind	0	0
/media/FILMS	/export/films	none	bind	0	0

```



if i view /export/tv or export/films I can see all my media files and subfolders no problem.

What am I missing so that the files and sub folders become visible?? I'm assuming its a permissions thing?

---

### Post by Guyver1 on 2011-05-02
ok I have installed ubuntu server 11.04 32bit on my server and configured nfs-kernel-server and confirmed it working on my ubuntu 10.10 64 bit workstation (see this thread - [http://ubuntuforums.org/showthread.php?t=1746839](http://ubuntuforums.org/showthread.php?t=1746839) )

So NFS shares are DEFINATELY working.

So my TVIX 4100SH media player has been configured to point to the films and data shares on the ubuntu server. 

When i select one of them to view, it connects, but the folder list is empty, cant see the sub folders and files in the shares.

anyone have any idea's on whether this is a permissions issue, or an nfs config issue???

How can i see the sub folders and files and play them without issue on my workstation but the media player cant see them??

any help appreciated!!

---

### Post by Guyver1 on 2011-05-02
found the answer here:

[http://epsilonprecision.com/index.php?option=com_content&view=article&id=46:linux-nfs-with-the-tvix-media-center&catid=34:tutorials&Itemid=53](http://epsilonprecision.com/index.php?option=com_content&view=article&id=46:linux-nfs-with-the-tvix-media-center&catid=34:tutorials&Itemid=53)

TVIX boxes can only read shares off the root /

](*,)](*,)](*,)](*,)](*,)

---

