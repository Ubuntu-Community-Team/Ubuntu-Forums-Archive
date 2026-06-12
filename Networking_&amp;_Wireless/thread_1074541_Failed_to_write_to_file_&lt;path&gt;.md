---
title: "Failed to write to file &lt;path&gt;"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by diwas on 2009-02-19
Failed to write to file <path> is displayed after 2-3 minutes i start downloading from Ktorrent. This happens with every torrent.
I tried Deluge but it also displays error "Status: Operation not Supported".

Transmission doesn't support selective downloads.
WINE+utorrent, i used to use it and it was perfect for me but again "Error: Request Not Supported" is displayed after sometime.

My target download folder is NTFS formatted. I tried changing it to / and Home folder, but still the problem persists. 

Please help me out. What to do?
I need a bittorent client which won't display any error and have selective downloads. 

I had another thread created quite a while ago, here the link:
[http://ubuntuforums.org/showthread.php?t=1057773](http://ubuntuforums.org/showthread.php?t=1057773)

Thank you.

---

### Post by diwas on 2009-02-20
Bump.

---

### Post by diwas on 2009-02-23
Guys, please help. I am unable to download any torrent through any software...

---

### Post by diwas on 2009-02-26
bump :s

---

### Post by diwas on 2009-02-27
bump...

BTW i googled a lot today. but still no results hehe..

i think this has no solution (sadly).

---

### Post by albinootje on 2009-02-27
> **diwas said:**
>  My target download folder is NTFS formatted. I tried changing it to / and Home folder, but still the problem persists.
Did you try writing to a new directory inside your home directory ?
By default a normal user is not allowed to write to /
Can you post the output of the following :
```

cat /etc/fstab
sudo fdisk -l
df -h

```

---

### Post by diwas on 2009-02-28
> **albinootje said:**
> Did you try writing to a new directory inside your home directory ?
By default a normal user is not allowed to write to /
Can you post the output of the following :
```

cat /etc/fstab
sudo fdisk -l
df -h

```
Yes, by / I mean inside Home. Sorry for the confusion.

I will give you the output as soon as I boot Ubuntu.

---

### Post by diwas on 2009-02-28
```

diwas@diwas-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=9bd5612f-8be6-4404-a0d6-e55c47cc09fa /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=f119f3d0-1ae0-4f62-8fc4-d0cc129f2667 none            swap    sw              0       0
# /dev/sda8
UUID=03f14472-967b-430d-a68a-5ba9d3664815 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1 /media/Root ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda5 /media/Music ntfs-3g force 0 0

```

```

diwas@diwas-desktop:~$ sudo fdisk -l
[sudo] password for diwas: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2f6b2f6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1697    13631121    7  HPFS/NTFS
/dev/sda2            1698        4865    25446960    f  W95 Ext'd (LBA)
/dev/sda5            1698        3525    14683378+   7  HPFS/NTFS
/dev/sda6            3526        4770    10000431   83  Linux
/dev/sda7            4771        4801      248976   82  Linux swap / Solaris
/dev/sda8            4802        4865      514048+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc84bc84b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2433    19543041    c  W95 FAT32 (LBA)
/dev/sdb2            2434        9729    58605120    f  W95 Ext'd (LBA)
/dev/sdb5            2434        4257    14651248+   b  W95 FAT32
/dev/sdb6            4258        7905    29302528+   b  W95 FAT32
/dev/sdb7            7906        9729    14651248+   b  W95 FAT32

```

```

diwas@diwas-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             9.4G  3.9G  5.1G  43% /
tmpfs                 251M     0  251M   0% /lib/init/rw
varrun                251M  208K  251M   1% /var/run
varlock               251M     0  251M   0% /var/lock
udev                  251M  2.8M  248M   2% /dev
tmpfs                 251M  424K  250M   1% /dev/shm
lrm                   251M  2.0M  249M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda1              13G  9.0G  4.1G  69% /media/Root
/dev/sda5              15G   14G  966M  94% /media/Music

```

---

### Post by diwas on 2009-03-02
bump

---

### Post by albinootje on 2009-03-02
> **diwas said:**
> ```

diwas@diwas-desktop:~$ cat /etc/fstab
--- cut ---
/dev/sda1 /media/Root ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda5 /media/Music ntfs-3g force 0 0

```

Thanks for the output.
Let's assume you're the only user on your Ubuntu system who wants to read and write to the NTFS-partitions, then make your /etc/fstab look like this :
```

/dev/sda1 /media/Root ntfs-3g rw,uid=1000,gid=1000,umask=000,locale=en_US.UTF-8 0 0
/dev/sda5 /media/Music ntfs-3g rw,force,uid=1000,gid=1000,umask=000 0 0

```
and perform :
```

sudo umount /dev/sda1
sudo umount /dev/sda5
sudo mount -a

```
And test it.

---

### Post by diwas on 2009-03-03
when i try to mount sda5, it shows the following error:
```

fuse: failed to access mountpoint /media/Music: No such file or directory


```

This is my target partition for torrents.

---

### Post by albinootje on 2009-03-03
> **diwas said:**
> 
```

fuse: failed to access mountpoint /media/Music: No such file or directory

```


What happens if you try again after doing this :
```

sudo mkdir /media/Music

```

---

### Post by diwas on 2009-03-03
Yes, the drive did mount after that. 
I tested the download through Ktorrent and after exactly 4minutes it said the same thing:
```

Error: Failed to write to file /media/Music/Bittorent/Saving Private Ryan/Saving_Private_Ryan.avi : Unknown Error
```

---

### Post by diwas on 2009-03-03
By the way, it's the same error I used to get before.

---

### Post by albinootje on 2009-03-04
> **diwas said:**
> ```

Error: Failed to write to file /media/Music/Bittorent/Saving Private Ryan/Saving_Private_Ryan.avi : Unknown Error
```

I assumed that your user was the first user you made during the Ubuntu installation, and therefore should have uid and gid 1000, is that correct ?
You can check that as following :
```

id

```
And can you post the output of :
```

mount

```

---

### Post by diwas on 2009-03-04
Yes
```

diwas@diwas-desktop:~$ id
uid=1000(diwas) gid=1000(diwas) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),1000(diwas)

```

And
```

diwas@diwas-desktop:~$ mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda1 on /media/Root type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5 on /media/Music type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/diwas/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=diwas)

```

---

### Post by diwas on 2009-03-09
bump

---

### Post by diwas on 2009-03-12
bump

---

### Post by diwas on 2009-03-17
..and bump again!

---

### Post by diwas on 2009-03-20
please help...:) 
bump

---

### Post by diwas on 2009-03-27
bump

---

### Post by diwas on 2009-04-11
Guys, arnt there anyway I could fix this? I dont want to reinstall. I still dont know the reason this has happened..and I guess i am the only one having this problem. 

Please help...

---

### Post by diwas on 2009-04-13
bump

---

### Post by basily on 2010-05-02
I am having a similar problem. I was using uTorrent without any trouble. I was running Karmic on an EXT3 partition, but saving all my torrents and data onto an NTFS drive. No problem everything was fine.

A couple of days ago, I upgraded to Lucid Lynx, and converted my EXT3 partition to an EXT4 partition. After the upgrade when I first ran uTorrent, I was forced to do an update (wine1.2-gecko if I remember right) and then uTorrent started up. I also updated uTorrent from version 2.0 build 18488, to version 2.0.1 build 19248.

Now every time I try to download a torrent, after a few minutes, I get the following error in the status of the torrent: "Error: Request not supported".

I tried reverting to uTorrent 2.0, and get the same error.

I tried various different torrents, same problem.

I tried using Deluge, and get a similar problem: it just says "Error X.XX%" under "Progress".

The problem goes away when I switch my download location to my EXT4 partition (instead of NTFS). But why should this problem all of a sudden appear when all the while I've been downloading to my NTFS partition without any trouble?

---

### Post by Chindokae on 2010-05-08
Same here.  Had been using uTorrent forever on 9.10 with no problem, download directory was on NTFS partition.  Upgraded to 10.04 and got these very same errors with the same versions of uTorrent.

Seems that certain Win32 apps are having trouble writing to NTFS from Wine.  uTorrent is known to have issues with Windows system caching.  That may have some bearing on this, or not.  Turning that feature off does not help.  

uTorrent only runs until it first tries to write to the target file, then it fails.  It never creates the file, so this may have something to do with how the file is being opened.

---

### Post by sw1sh on 2010-05-10
I'm using Transmission and after upgrading to Ubuntu LST I'm getting "Operation not supported" right after downloading every torrent on my ntfs partition(ext4 is ok). Before upgrading i could do it with excessive CPU usage, but now i cant even start to download my torrents. Same error even when i downloading files with Firefox DownloadHelper plugin.

I think it is due ntfs-3g plugin can't preoccupy disk space, it is what all download software do.

---

### Post by zamarax on 2010-05-16
I'm also having this issue with ubuntu 10.04, using deluge and downloading to a NTFS partition, however even when switching it to a ext4 partition and my home folder it still happens, 10.04 bug?

---

### Post by Paul-Devon-UK on 2010-05-21
> **zamarax said:**
> I'm also having this issue with ubuntu 10.04, using deluge and downloading to a NTFS partition, however even when switching it to a ext4 partition and my home folder it still happens, 10.04 bug?

That's encouraging :confused:

10.04+wine+utorrent here and seeing this issue in the last couple of days. Some update has 'fixed' this I guess but with the constant stream of updates on a daily basis I wouldn't know where to start. Maybe the Microsoft Patch Tuesday system has advantages?

---

### Post by Wolfhowell on 2010-05-25
Add one more system with the problem.

Unable to download to an NTFS partition, but on ext4 seems fine. As a workaround I have it downloading to the home folder and then moving when completed to the NTFS partition. All seems to be well. I can also confirm problem only started happening when I upgraded from karmic to lucid.

Deluge Version: 1.2.2
libtorrent version: 0.14.10.0

---

