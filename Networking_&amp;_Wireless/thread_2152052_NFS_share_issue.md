---
title: "NFS share issue"
date: 2013-06-06
forum: Networking &amp; Wireless
---

### Post by cscj01 on 2013-06-06
I am running Ubuntu 12.04 x64 on one PC (cp1) and 12.04 x32 on the other (cp2).  Both machines are dual boot with XP being the first partition on the boot disk.  I have NFS server on cp2 and NFS client on cp1.  For quite a while, I have been using a share that is a USB drive with an NTFS file system on cp2.  I now have a need to share a directory on the XP partition.  I entered the required entry in /etc/exports for the new directory and re-exported my shares.  I received a message saying the new share was not exported.  I rebooted the machine and the message did not appear.  However, when I use```
showmount -a
```on the client (cp1), I get the following```
All mount points on cp2
192.168.1.100:/media/Ubuntu_Data_Backup/Data
192.168.1.114:/media/Ubuntu_Data_Backup/Data
```If I enter```
exportfs -a
```on the server (cp2), I receive the following```
exportfs: Failed to stat /media/Charsar_Sys/Documents and Settings/All Users/Documents: No such file or directory
```My entries in /etc/exports are```
/media/Ubuntu_Data_Backup/Data 192.168.1.0/24(async,no_root_squash,no_subtree_check,rw)
"/media/Charsar_Sys/Documents and Settings/All Users/Documents" 192.168.1.0/24(async,no_root_squash,no_subtree_check,rw)

```If I then check the /media directory, Charsar_Sys is not there.  However, If I check to see if it is mounted, it is mounted.  If I then check /media again, it is there.

My impression is that the first mount point is being exported twice; once for the first share, and once for the second share.  If I run```
df -h
```on the client (cp1), the only mount related to the NFS server that appears is```
cp2.local:/media/Ubuntu_Data_Backup/Data  1.4T  896G  502G  65% /mn
```Hopefully someone can tell me where I am going wrong.  Thanks for any help rendered.

---

### Post by cscj01 on 2013-06-07
So here is further information.  When I use the command```
exportfs -a
```on the server (cp2), I now get the message ```
exportfs: Warning: /media/Charsar_Sys/Documents and Settings/Documents does not support NFS export.
```I presume that Charsar_Sys is in the /media directory at this time as opposed to the previous attempt above, and, in fact, has been showing up there whenever I browse to /media.

Charsar_Sys is the name of the system HDD on cp2.  However, the other share, /media/Ubuntu_Data_Backup/Data, is a USB HDD named Ubuntu_Data_Backup.  Both are NTFS file systems.  The only difference is one (the share that fails) is an internal HDD, and the other (the share that works) is a USB HDD.  Well, there is another difference: the failing one has spaces in the path, whereas the successfull one does not.  But neither of these should make a difference as far as I can ascertain.

---

### Post by SeijiSensei on 2013-06-07
Is [no_root_squash]("http://ubuntuforums.org/showthread.php?t=1791330&p=11190024&viewfull=1#post11190024") included as an option in both exports?

---

### Post by LewisTM on 2013-06-07
How is your Charsar_Sys NTFS partition mounted on the server? From /etc/fstab?
I doubt anything automounted on click would constitute a valid NFS export.

Cheers!

---

### Post by cscj01 on 2013-06-07
> **SeijiSensei said:**
> Is [no_root_squash]("http://ubuntuforums.org/showthread.php?t=1791330&p=11190024&viewfull=1#post11190024") included as an option in both exports?

Yes, see initial entry.

> **LewisTM said:**
> How is your Charsar_Sys NTFS partition mounted on the server? From /etc/fstab?
I doubt anything automounted on click would constitute a valid NFS export.

Cheers!The only entries in /etc/fstab on the server (cp2) are the Ubuntu ext4 and the swap partitions.  I have no trouble sharing the USB NTFS HD on cp2.  Why would the other HD be any different?  I do know all HD volumes are in the Places Menu upon boot, and they stay there unless I specifically unmount them.  Are you suggesting that I include an entry in /etc/fstab for Charsar_Sys?

---

### Post by LewisTM on 2013-06-07
By default, any partition that is not in fstab will only get mounted on request, from Places or a file manager. That means they are not accessible for sharing at startup. Plus this kind of automounting uses subsystems like udisks and gio that slam permission restrictions on certain filesystem types, which might explain your error with the export process.
So yes, I suggest you enter your partition in fstab. I'm not a specialist on NTFS but you should set the mount options to be as permissive as possible.

I don't know how you managed to share the USB drive without mounting it first. Perhaps the subdirectory you export in /media is also present when the drive is unmounted, so you get away with it error-free. 
Best to always have drives ready at boot when running an NFS server. The convoluted Ubuntu point-and-click mounting scheme is not meant for server setups.

---

### Post by cscj01 on 2013-06-08
> **LewisTM said:**
> By default, any partition that is not in fstab will only get mounted on request, from Places or a file manager. That means they are not accessible for sharing at startup. Plus this kind of automounting uses subsystems like udisks and gio that slam permission restrictions on certain filesystem types, which might explain your error with the export process.
So yes, I suggest you enter your partition in fstab. I'm not a specialist on NTFS but you should set the mount options to be as permissive as possible.

I don't know how you managed to share the USB drive without mounting it first. Perhaps the subdirectory you export in /media is also present when the drive is unmounted, so you get away with it error-free. 
Best to always have drives ready at boot when running an NFS server. The convoluted Ubuntu point-and-click mounting scheme is not meant for server setups.

Well, I put all the hard disks on cp2 into /etc/fstab using their UUID.  Now, when I try to export my shares, I get the message ```
exportfs: Warning: /media/Charsar_Sys/Documents and Settings/All Users/Documents does not support NFS export.
```When I use ```
sudo showmount -a cp2
``` on the client cp2, I get ```
All mount points on cp2:
192.168.1.100:/media/Ubuntu_Data_Backup/Data
192.168.1.114:/media/Ubuntu_Data_Backup/Data
```For some funky reason, both shares are using the same mount point, even though they are different .  So here I am lost again.

---

### Post by LewisTM on 2013-06-10
Sorry for the late reply.
For reloading /etc/exports into the NFS daemon, you should run
```
sudo exportfs -ra
```
Your command [FONT=Courier New]showmount -a[/FONT] shows which clients are accessing and mounting a share from a specific host. In your case there are two machines, both mounting the same share, so nothing wrong here.

You might be looking for 
```
showmount -e [host]
```
That will show you what shares are available on a specific host.

Not sure about the refusal to share the NTFS folder. Two things to try:
1) Share the topmost level on the HDD (/media/Charsar_Sys), so you don't introduce spaces in the config.
2) Tweak the NTFS permissions. Please post the output of [FONT=Courier New]mount [/FONT]so we can have a look at how your HDD and USB disks are mounted on the server.

Thanks!

---

### Post by cscj01 on 2013-06-12
Here is the output from```
mount
```on the server```
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtempfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid, nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid, nodev)
/dev/sda2 on media/Charsar_Sys type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on media/Data_001 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on media/Ubuntu_Data_Backup type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd1 on media/Data1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
rpc_pipefs on /run/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
gvfs-fuse-daemon on /home/brenda/.gvfs type fuse.gvfs.daemon (rw,nosuid,nodev,user=brenda)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs.daemon (rw,nosuid,nodev)
```After issuing```
sudo exportfs -ra
```on cp2 and getting the same message as before```
exportfs: Warning: /media/Charsar_Sys/Documents and Settings/All Users/Documents does not support NFS export
```I then issued```
showmount -e cp2
``` on the client, I received the following:```
Export list for cp2:
/media/Charsar_Sys/Documents and Settings/All Users/Documents 192.168.1.0/24
/media/Ubuntu_Data_Backup/Data                                192.168.1.0/24
```However, when I give the command```
mount -a
```from the client, I get the following:```
[mntent]: line 17 in /etc/fstab is bad

```Line 17 in /etc/fstab is```
cp2.local:"/media/Charsar_Sys/Documents and Settings/All Users/Documents" /mnt/cp2_shared_docs nfs _netdev,vers=3 0 0
```So it seems I am getting closer.  And cp2_shared_docs does exist in /mnt on the client.

I can change the share to /media/Charsar_Sys, but what are the options that will allow me to access the subdirectories?  I assume two are no_root_squash and no_subtree_check.  Are there any others of which I should be aware?

Edit:  I changed the share to /media/Charsar_Sys on the server and made the appropriate change in /etc/fstab on the client and all is well Thanks for all your help.

---

