---
title: "Mounting bound directories over nfs"
date: 2012-05-24
forum: Networking &amp; Wireless
---

### Post by ChrisCummins on 2012-05-24
Hi,
I am trying to configure a simple file server for home use between Ubuntu machines using nfs. I am trying to share the contents of 2 volumes '2TBA' and '2TBB', however on the client side I can only see the directories, the contents are empty. On the server side everything looks fine.

**Server side configuration**
The two volumes are mounted to /mnt/2TBA and /mnt/2TBB. Additionally, the following bindings are made:

*/etc/fstab*
```

/mnt/2TBA  /server/2TBA    none    bind 0 0
/mnt/2TBB  /server/2TBB    none    bind 0 0

```

Access to these filesystems is set as:

*/etc/exports*
```
/server          *(rw,fsid=0,insecure,no_subtree_check,async)
/server/2TBA     *(rw,fsid=0,insecure,no_subtree_check,async)
/server/2TBB     *(rw,fsid=0,insecure,no_subtree_check,async)
```

**Client side configuration**
Mounting of the nfs system is set by:

*/etc/fstab*
```
beast:/  /beast  nfs4  _netdev  0 0
```


'mount -a' returns no errors and navigating the /beast directory shows the two '2TB*' folders, just not their contents. It seems like those mounts are getting masked off in some way. Any files in the /server directory show up on the client just fine.

I am using nfs4 on Ubuntu 12.04. Any help would be greatly appreciated

Regards
Chris

---

### Post by CampbellBoyd on 2012-12-14
I've the same problem. Apart form the folders being present but empty on the client PC, if I save a file to one of them, it does not appear 0n the server. 

I'm sharing the users' home folders the same way and they show up with files and folders ok.

Mount -a gives:
/dev/sda5 on /media/SBackupdrive type ext4 (rw,errors=remount-ro) [SBackupdrive]
/dev/sda9 on /media/DriveforDesktopBackup type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) [DriveforDesktopBackup]
/home on /export/home type none (rw,bind)
/media/DriveforDesktopBackup/SharedFiles on /export/home/SharedFiles type none (rw,bind)
/media/DriveforDesktopBackup/SharedPictures on /export/home/SharedPictures type none (rw,bind)

The first two lines are the drivers being mounted and the next three the home folder and then the mounted drives being loaded into export.

---

### Post by dannyboy79 on 2012-12-14
> **ChrisCummins said:**
> Hi,
I am trying to configure a simple file server for home use between Ubuntu machines using nfs. I am trying to share the contents of 2 volumes '2TBA' and '2TBB', however on the client side I can only see the directories, the contents are empty. On the server side everything looks fine.

**Server side configuration**
The two volumes are mounted to /mnt/2TBA and /mnt/2TBB. Additionally, the following bindings are made:

*/etc/fstab*
```

/mnt/2TBA  /server/2TBA    none    bind 0 0
/mnt/2TBB  /server/2TBB    none    bind 0 0

```

Access to these filesystems is set as:

*/etc/exports*
```
/server          *(rw,fsid=0,insecure,no_subtree_check,async)
/server/2TBA     *(rw,fsid=0,insecure,no_subtree_check,async)
/server/2TBB     *(rw,fsid=0,insecure,no_subtree_check,async)
```

**Client side configuration**
Mounting of the nfs system is set by:

*/etc/fstab*
```
beast:/  /beast  nfs4  _netdev  0 0
```


'mount -a' returns no errors and navigating the /beast directory shows the two '2TB*' folders, just not their contents. It seems like those mounts are getting masked off in some way. Any files in the /server directory show up on the client just fine.

I am using nfs4 on Ubuntu 12.04. Any help would be greatly appreciated

Regards
ChrisI must be misunderstanding something here, you're exporting 3 directories (which there's no need to export the second 2 since they'll be exported within /server) 
/server
/server/2TBA
/server/2TBB
yet your fstab doesn't mount any of those folders?

---

### Post by dannyboy79 on 2012-12-14
> **CampbellBoyd said:**
> I've the same problem. Apart form the folders being present but empty on the client PC, if I save a file to one of them, it does not appear 0n the server. 

I'm sharing the users' home folders the same way and they show up with files and folders ok.

Mount -a gives:
/dev/sda5 on /media/SBackupdrive type ext4 (rw,errors=remount-ro) [SBackupdrive]
/dev/sda9 on /media/DriveforDesktopBackup type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) [DriveforDesktopBackup]
/home on /export/home type none (rw,bind)
/media/DriveforDesktopBackup/SharedFiles on /export/home/SharedFiles type none (rw,bind)
/media/DriveforDesktopBackup/SharedPictures on /export/home/SharedPictures type none (rw,bind)

The first two lines are the drivers being mounted and the next three the home folder and then the mounted drives being loaded into export.let's see your /etc/exports file from the server and then your fstab from the client

---

### Post by CampbellBoyd on 2012-12-14
> **dannyboy79 said:**
> let's see your /etc/exports file from the server and then your fstab from the client

exports:
/export/home            192.168.1.100/192.168.1.104(rw,fsid=0,nohide,no_subtree_check,sync)
/export/home/SharedPictures  192.168.1.100/192.168.1.104(rw,fsid=0,nohide,no_subtree_check,sync)
/export/home/SharedFiles     192.168.1.100/192.168.1.104(rw,fsid=0,nohide,no_subtree_check,sync)

client fstab:
UUID=77d40098-9bd1-446d-b32f-f36de3032d1a swap swap sw 0 0
UUID=28e8ccf2-0784-4ced-8596-5277bc02e26c / ext4 defaults 0 1
192.168.1.100:/ /home/server nfs4 auto 0 0

The folders are now missing on the client, i.e. not appearing at all. Looking at the server folder with Nautilus has a comment "(some contents unreadable)"

---

### Post by dannyboy79 on 2012-12-14
if you share /export/home that is good enough, you don't need to share any subfolders AFAIK. Also, your client needs to be 
```
192.168.1.100:/export/home /home/server nfs4 auto 0 0
```

---

### Post by CampbellBoyd on 2012-12-14
> **dannyboy79 said:**
> if you share /export/home that is good enough, you don't need to share any subfolders AFAIK. Also, your client needs to be 
```
192.168.1.100:/export/home /home/server nfs4 auto 0 0
```

Thanks. The first suggestion I implemented and there is no change.
The second results in the following error:
mount.nfs4: mounting 192.168.1.100:/export/home failed, reason given by server:
  No such file or directory

I think with nfs4 it automatically looks at /export.
I've also tried mounting the drives to /mnt rather than /media but this made no difference.

---

### Post by dannyboy79 on 2012-12-14
are you sure your server is 192.168.1.100? what does this command return?
```
showmount -e 192.168.1.100
```

---

### Post by CampbellBoyd on 2012-12-14
> **dannyboy79 said:**
> are you sure your server is 192.168.1.100? what does this command return?
```
showmount -e 192.168.1.100
```

Thanks for your help.

showmount -e returns:
clnt_create: RPC: Port mapper failure - Unable to receive: errno 111 (Connection refused)

server is definitely 192.168.1.100

---

### Post by dannyboy79 on 2012-12-14
have you installed nfs-common on the client? whats the IP of your client? it appears as though it may be out of the range that your allowing in your exports file on the server otherwise showmount -e would NOT have failed connection, it would have listed out the nfs shares available. try sharing to the entire subnet using this in your exports instead just for troubleshooting sake.
```
/export/home 192.168.1.100/24(rw,fsid=0,nohide,no_subtree_check,sy nc)
```

you'll have to issue the following to re-export the filesystems
```
sudo service nfs-kernel-server restart
```

---

### Post by CampbellBoyd on 2012-12-14
> **dannyboy79 said:**
> have you installed nfs-common on the client? whats the IP of your client? it appears as though it may be out of the range that your allowing in your exports file on the server otherwise showmount -e would NOT have failed connection, it would have listed out the nfs shares available. try sharing to the entire subnet using this in your exports instead just for troubleshooting sake.
```
/export/home 192.168.1.100/24(rw,fsid=0,nohide,no_subtree_check,sy nc)
```

you'll have to issue the following to re-export the filesystems
```
sudo service nfs-kernel-server restart
```

nfs-common is installed on client.
the client PC I'm using for testing is 192.168.1.103 - i.e. within range. Also, if it was not in range then the home folders would not be seen on the client, I think. 

What is different between the exports that are successful and those that are not is that the unsuccessful ones are partitions mounted into /mount. 

Incidentally, when I look in these shares on the server, both in /mount and /export I can see all the files that are there.

---

### Post by dannyboy79 on 2012-12-14
i'm at a loss here. I don't use a range like you're using in your exports file and I am very confused why showmount -e doesn't work, something is not right. It should be irrelevant what paths/folders are being exported from the server, whether they are in export or mnt or mount. I have a folder shared via nfs from /var/lib/ and others from /media.

what happens if you try this?
```
/export/home 192.168.1.103 (rw,fsid=0,nohide,no_subtree_check,sync)
```

then restart the nfs-kernel-server, and see if showmount -a works then from the 192.168.1.103 client. 

So you're saying you have some NFS shares that are working?

---

### Post by LewisTM on 2012-12-14
CampbellBoyd,

I hope I can help you. Let's look at what you are doing right and wrong

Right:
- Bind mounts to build your /server export tree
- fsid=0 for your NFS root directory
- nohide for your child, bound directories

Wrong:
- fsid=0 for your child dirs. Only the root needs this, to set it as '/'
- 192.168.1.100/192.168.1.104 for an IP range. NFS doesn't work like that. The slash it to specify the mask, not the upper limit of a range.

Given those issues, your exports should be
> /export/home 192.168.1.100/29(rw,fsid=0,nohide,no_subtree_check,sync)
/export/home/SharedPictures 192.168.1.100/29(rw,nohide,no_subtree_check,sync)
/export/home/SharedFiles 192.168.1.100/29(rw,nohide,no_subtree_check,sync)
Then reload the NFS exports
```
sudo exportfs -ra
```
Cheers!

---

### Post by steeldriver on 2012-12-14
It kind of looks like you are blocking the portmapper port (111) on your server - do you have custom iptables / ufw rules enabled?

> **CampbellBoyd said:**
> 
showmount -e returns:
clnt_create: RPC: Port mapper failure - Unable to receive: errno 111 (Connection refused)


[http://tldp.org/HOWTO/NFS-HOWTO/security.html](http://tldp.org/HOWTO/NFS-HOWTO/security.html)

---

### Post by CampbellBoyd on 2012-12-15
> **dannyboy79 said:**
> i'm at a loss here. I don't use a range like you're using in your exports file and I am very confused why showmount -e doesn't work, something is not right. It should be irrelevant what paths/folders are being exported from the server, whether they are in export or mnt or mount. I have a folder shared via nfs from /var/lib/ and others from /media.

what happens if you try this?
```
/export/home 192.168.1.103 (rw,fsid=0,nohide,no_subtree_check,sync)
```

then restart the nfs-kernel-server, and see if showmount -a works then from the 192.168.1.103 client. 

So you're saying you have some NFS shares that are working?

I did this but still get showmount -e returns:
clnt_create: RPC: Port mapper failure - Unable to receive: errno 111 (Connection refused)

Yes - the users' folders in home are shared. It is only the two folders from the drive mount in /mount that appear but empty.

---

### Post by CampbellBoyd on 2012-12-15
> **LewisTM said:**
> CampbellBoyd,

I hope I can help you. Let's look at what you are doing right and wrong

Right:
- Bind mounts to build your /server export tree
- fsid=0 for your NFS root directory
- nohide for your child, bound directories

Wrong:
- fsid=0 for your child dirs. Only the root needs this, to set it as '/'
- 192.168.1.100/192.168.1.104 for an IP range. NFS doesn't work like that. The slash it to specify the mask, not the upper limit of a range.

Given those issues, your exports should be

Then reload the NFS exports
```
sudo exportfs -ra
```
Cheers!

Thanks LewisTM

I've changed export file as you suggest and reloaded and there is no change - the users's folders in home are there and populated, the Sharedfiles and SharePicturs are there but empty.

---

### Post by dannyboy79 on 2012-12-15
the folders will be there because you created them. post your exports file again and your fstab entries.

---

### Post by CampbellBoyd on 2012-12-15
> **dannyboy79 said:**
> the folders will be there because you created them. post your exports file again and your fstab entries.
exports:
/export/home            192.168.1.100/29(rw,fsid=0,nohide,no_subtree_check,sync)
#/export/home/SharedPictures  192.168.1.100/29(rw,nohide,no_subtree_check,sync)
#/export/home/SharedFiles     192.168.1.100/29(rw,nohide,no_subtree_check,sync)

uncommenting the 2nd and 3rd lines makes no difference.

fstab:
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=e0a1763d-1632-4801-96ab-67d67ec86c84 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda11 during installation
UUID=6f78ce23-11c3-440d-99d5-c1f097ca810d none            swap    sw              0       0
/dev/sda5 /media/SBackupdrive               ext4    errors=remount-ro 0       1
/dev/sda9 /media/DriveforDesktopBackup   ntfs   errors=remount-ro 0       1 
/home                                       /export/home none    bind  0  0 
/media/DriveforDesktopBackup/SharedPictures /export/home/SharedPictures none bind 0 0 
/media/DriveforDesktopBackup/SharedFiles    /export/home/SharedFiles none bind 0 0

---

### Post by LewisTM on 2012-12-15
I believe you are trying to export folders found on an NTFS drive. I think you need to add no_root_squash as an export option for those.

---

### Post by CampbellBoyd on 2012-12-17
> **LewisTM said:**
> I believe you are trying to export folders found on an NTFS drive. I think you need to add no_root_squash as an export option for those.

Success!!

Many thanks to all offered their assistance.

---

### Post by LewisTM on 2012-12-17
Awesome!
Please use the Thread Tools and mark as SOLVED.

---

### Post by singedwings on 2012-12-18
Thanks to all for this post it got me sorted out! I had trouble trying to export the mount points for ext4 hard drives. I got around this by exporting a subfolder of these mounts. Is there an option to overcome this without resorting to subfolders?

---

### Post by LewisTM on 2012-12-18
The OP's problem was NTFS and that is not your case; you seem to have a different problem. You should be able to export any directory with the proper setup. 

How about you start a new thread and provide the usual /etc/fstab and /etc/exports contents and we'll see what we can do.

---

