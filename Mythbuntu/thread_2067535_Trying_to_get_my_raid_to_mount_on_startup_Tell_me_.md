---
title: "Trying to get my raid to mount on startup Tell me if this is correct?"
date: 2012-10-07
forum: Mythbuntu
---

### Post by RTIInstaller on 2012-10-07
I want my raid drive to mount at startup. Right now it behaves like an external drive, I have to click on the icon after start up to get it to mount and it asks for a password each time.  Can I get around this with this command  sda1 or sda5 I am not sure? gvfs-mount -d /dev/sda1
   
    
   
   
  cat /etc/mtab
  /dev/sda1 / ext4 rw,errors=remount-ro 0 0
  proc /proc proc rw,noexec,nosuid,nodev 0 0
  sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
  none /sys/fs/fuse/connections fusectl rw 0 0
  none /sys/kernel/debug debugfs rw 0 0
  none /sys/kernel/security securityfs rw 0 0
  udev /dev devtmpfs rw,mode=0755 0 0
  devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
  tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
  none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
  none /run/shm tmpfs rw,nosuid,nodev 0 0
  rpc_pipefs /run/rpc_pipefs rpc_pipefs rw 0 0
  nfsd /proc/fs/nfsd nfsd rw 0 0
  /dev/sdc1 /media/FreeAgent\040GoFlex\040Drive fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
   
  /dev/sda1: UUID="d80b81b8-3030-46e4-b2e7-b70e802f5281" TYPE="ext4" 
  /dev/sda5: UUID="53036505-44bb-4009-b519-bffe4324d5ff" TYPE="swap" 
  /dev/sdc1: LABEL="FreeAgent GoFlex Drive" UUID="E6404B75404B4B8D" TYPE="ntfs" 
  /dev/sdb1: UUID="3d6c407c-1527-4fcf-866f-50384add4c01" TYPE="ext2"
   
  # <file system> <mount point>   <type>  <options>       <dump>  <pass>
  proc            /proc           proc    nodev,noexec,nosuid 0       0
  # / was on /dev/sda1 during installation
  UUID=d80b81b8-3030-46e4-b2e7-b70e802f5281 /               ext4    errors=remount-ro 0       1
  # swap was on /dev/sda5 during installation
  UUID=53036505-44bb-4009-b519-bffe4324d5ff none            swap    sw              0       0
   
  mount
  /dev/sda1 on / type ext4 (rw,errors=remount-ro)
  proc on /proc type proc (rw,noexec,nosuid,nodev)
  sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
  none on /sys/fs/fuse/connections type fusectl (rw)
  none on /sys/kernel/debug type debugfs (rw)
  none on /sys/kernel/security type securityfs (rw)
  udev on /dev type devtmpfs (rw,mode=0755)
  devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
  tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
  none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
  none on /run/shm type tmpfs (rw,nosuid,nodev)
  rpc_pipefs on /run/rpc_pipefs type rpc_pipefs (rw)
  nfsd on /proc/fs/nfsd type nfsd (rw)
  /dev/sdc1 on /media/FreeAgent GoFlex Drive type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
  /dev/sdb1 on /media/3d6c407c-1527-4fcf-866f-50384add4c01__ type ext2 (rw,nosuid,nodev,uhelper=udisks)

---

### Post by nickrout on 2012-10-07
What is this "raid drive"? How does it plug into the system.

Looks like it might be an external plug in (usb?) drive? Which device is it in your output? I suspect the freeagent drive, but you just aren't being specific, despite my earlier requests in your other threads for you to be specific.

Anyway, I believe external drives are best mounted by finding the UUID and then putting an entry in /etc/fstab.

tell us definitely which device (/dev/sd??) you are trying to mount and the output of ```
sudo blkid
``` and I'll tell you what to put in /etc/fstab.

---

### Post by RTIInstaller on 2012-10-07
> **nickrout said:**
> What is this "raid drive"? How does it plug into the system.

Looks like it might be an external plug in (usb?) drive? Which device is it in your output? I suspect the freeagent drive, but you just aren't being specific, despite my earlier requests in your other threads for you to be specific.

Anyway, I believe external drives are best mounted by finding the UUID and then putting an entry in /etc/fstab.

tell us definitely which device (/dev/sd??) you are trying to mount and the output of ```
sudo blkid
``` and I'll tell you what to put in /etc/fstab.

/dev/sda1: UUID="d80b81b8-3030-46e4-b2e7-b70e802f5281" TYPE="ext4" 
/dev/sda5: UUID="53036505-44bb-4009-b519-bffe4324d5ff" TYPE="swap" 
/dev/sdb1: LABEL="FreeAgent GoFlex Drive" UUID="E6404B75404B4B8D" TYPE="ntfs" 
/dev/sdc1: UUID="3d6c407c-1527-4fcf-866f-50384add4c01" TYPE="ext2" 


This is an internal 8 drive raid 5 PCI card setup

---

### Post by nickrout on 2012-10-07
so I'll ask again, please pay attention.

Which drive is the RAID drive?

/dev/sdb1 or /dev/sdc1.

---

### Post by RTIInstaller on 2012-10-08
> **nickrout said:**
> so I'll ask again, please pay attention.

Which drive is the RAID drive?

/dev/sdb1 or /dev/sdc1.

I am sorry nick it is sdc1 :wink:

I dont know what /dev/sda5: is  I only have three drives   1.5 TB from my operating system and for additional storage, the free agent external drive, and the raid that was originally set up as ext2 I would wipe it and start over but it has 3.9 TB of movies on it

---

### Post by nickrout on 2012-10-08
> **RTIInstaller said:**
> I am sorry nick it is sdc1 :wink:

I dont know what /dev/sda5: is  I only have three drives   1.5 TB from my operating system and for additional storage, the free agent external drive, and the raid that was originally set up as ext2 I would wipe it and start over but it has 3.9 TB of movies on it
sda5 is swap, which is place where the OS pages RAM out to when there is not enough physical RAM for all the processes running. It's slower than RAM obviously, but better than crashing out for lack or RAM.

Now make a place for the drive to mount permanently and 

```
sudo mkdir /mnt/raid
```

then edit /etc/fstab to add the following line at the end:

```
UUID=3d6c407c-1527-4fcf-866f-50384add4c01 /mnt/raid ext2 defaults 0 1
```

This should mount the raid drive to /mnt/raid on every boot.

---

### Post by RTIInstaller on 2012-10-08
> **nickrout said:**
> sda5 is swap, which is place where the OS pages RAM out to when there is not enough physical RAM for all the processes running. It's slower than RAM obviously, but better than crashing out for lack or RAM.

Now make a place for the drive to mount permanently and 

```
sudo mkdir /mnt/raid
```then edit /etc/fstab to add the following line at the end:

```
UUID=3d6c407c-1527-4fcf-866f-50384add4c01 /mnt/raid ext2 defaults 0 1
```This should mount the raid drive to /mnt/raid on every boot.

Thanks Nick!

After I did what you suggested I entered sudo fdisk -l
 
And this is what I got below. I am going to restart my machine in about 20 minutes, its busy sorting out its movie database right now :razz:

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002581d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  2928197631  1464097792   83  Linux
/dev/sda2      2928199678  2930276351     1038337    5  Extended
/dev/sda5      2928199680  2930276351     1038336   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 4499.9 GB, 4499932446720 bytes
255 heads, 63 sectors/track, 547085 cylinders, total 8788930560 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT

Disk /dev/sdc: 2000.4 GB, 2000398933504 bytes
1 heads, 63 sectors/track, 62016335 cylinders, total 3907029167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x55c3ffbc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  3907024127  1953512032+   7  HPFS/NTFS/exFAT
aaron@aaron-NY542AA-ABA-s5220f:~$ sudo mkdir /mnt/raid
aaron@aaron-NY542AA-ABA-s5220f:~$ UUID=3d6c407c-1527-4fcf-866f-50384add4c01 /mnt/raid ext2 defaults 0 1
-bash: /mnt/raid: Is a directory
aaron@aaron-NY542AA-ABA-s5220f:~$ sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002581d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  2928197631  1464097792   83  Linux
/dev/sda2      2928199678  2930276351     1038337    5  Extended
/dev/sda5      2928199680  2930276351     1038336   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 4499.9 GB, 4499932446720 bytes
255 heads, 63 sectors/track, 547085 cylinders, total 8788930560 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT

Disk /dev/sdc: 2000.4 GB, 2000398933504 bytes
1 heads, 63 sectors/track, 62016335 cylinders, total 3907029167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x55c3ffbc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  3907024127  1953512032+   7  HPFS/NTFS/exFAT

---

### Post by RTIInstaller on 2012-10-09
> **nickrout said:**
> sda5 is swap, which is place where the OS pages RAM out to when there is not enough physical RAM for all the processes running. It's slower than RAM obviously, but better than crashing out for lack or RAM.

Now make a place for the drive to mount permanently and 

```
sudo mkdir /mnt/raid
```then edit /etc/fstab to add the following line at the end:

```
UUID=3d6c407c-1527-4fcf-866f-50384add4c01 /mnt/raid ext2 defaults 0 1
```This should mount the raid drive to /mnt/raid on every boot.

works great :guitar:

---

### Post by BrandonXavier on 2012-10-09
Are you sure you have your drives right?  sdb1 is the one with ~4TB of storage, while sdc1 has ~2TB (assuming your 3.9TB of movies are all on the same partition)

---

### Post by nickrout on 2012-10-09
> **BrandonXavier said:**
> Are you sure you have your drives right?  sdb1 is the one with ~4TB of storage, while sdc1 has ~2TB (assuming your 3.9TB of movies are all on the same partition)Actually the device names have changed between posts (this can easily happen which is why UUIDs are so good).

---

### Post by RTIInstaller on 2012-10-10
> **nickrout said:**
> Actually the device names have changed between posts (this can easily happen which is why UUIDs are so good).


I think brandon is correct,  It is the 4TB that I am trying to mount and I am still having problem with this  :-( my bad so it would be sdb1

Could also be a permissions issu as everytime I manual click on the raid logo on the desk top it asks for a password?

---

### Post by RTIInstaller on 2012-10-11
Yes my problem is permissions, it wont mount the sdc1 drive until the password is entered

sudo blkid
/dev/sda1: UUID="d80b81b8-3030-46e4-b2e7-b70e802f5281" TYPE="ext4" 
/dev/sda5: UUID="53036505-44bb-4009-b519-bffe4324d5ff" TYPE="swap" 
/dev/sdb1: LABEL="FreeAgent GoFlex Drive" UUID="8EE008B5E008A595" TYPE="ntfs" 
/dev/sdc1: UUID="3d6c407c-1527-4fcf-866f-50384add4c01" TYPE="ext2" 
/dev/sr0: LABEL="<Precious>" TYPE="udf" 

How do I remove permissions or auto enter the password on startup?
):P

---

