---
title: "Ipod mounted readonly"
date: 2011-03-23
forum: Multimedia Software
---

### Post by markp1989 on 2011-03-23
trying to put some music on my dads ipod, and keep getting nagged about it being a read only file system.

mtab shows it as readonly , but I still cannot write to it
```
 
mark@mark-desktop:~$ cat /etc/mtab
/dev/sda1 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
/dev/sda2 /home ext4 rw,commit=0 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/mark/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=mark 0 0
/dev/sdb1 /media/NICKY'S\040IPO vfat rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush 0 0
mark@mark-desktop:~$ 

```

I did a quick google search, found a bunch of threads about 5 years old.

one suggested dosfsck /dev/sdb1 -a which didnt help 

any pointers?

Thanks, mark

---

### Post by markp1989 on 2011-03-23
ok, this is just stupid.....


I made a manual entry in fstab to mount the ipod rw , confirmed that I could make a new file on the ipod.

I open rhythmbox still cant copy music across , says its still read only!!!!!! so i open up nautilus again, and now I cannot make any more files on the ipod, I dont see how opening rhythmbox can make the ipod suddenly become readonly!! ??

Any one got any ideas?

---

### Post by Chronon on 2011-03-23
Actually, the data partition is the second one.  The firmware is on the first partition but since it's a raw partition you can't fsck it.  To repair the data partition and allow it to be mounted normally, try doing 
```
fsck.vfat -a /dev/sdb2
```

---

### Post by markp1989 on 2011-03-23
> **Chronon said:**
> Actually, the data partition is the second one.  The firmware is on the first partition but since it's a raw partition you can't fsck it.  To repair the data partition and allow it to be mounted normally, try doing 
```
fsck.vfat -a /dev/sdb2
```

there isnt an sdb2 :S 

I was also under the impression that the data partition would be the 2nd one, but it appears to only have 1 partition (sdb1) which is roughly 8gb in size

the strange thing is, I can manually add files to the ipod straight after mounting it (obviously the ipod doesnt add them to the library) , but as soon as I try to use rhythmbox or gtkpod the drive becomes readonly, even to the standard file manager :S


edit 
```


Disk /dev/sdb: 7971 MB, 7971016704 bytes
35 heads, 41 sectors/track, 1356 cylinders
Units = cylinders of 1435 * 4096 = 5877760 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1357     7783940    b  W95 FAT32
Partition 1 does not start on physical sector boundary.
mark@mark-desktop:~$ 


```

---

### Post by Chronon on 2011-03-24
What kind of iPod is it?  Does Apple's firmware boot?

I'm mostly familiar with 1g through 5.5g iPods (including Mini 1g/2g and Nano 1g/2g): The MBR should list a raw partition and a (FAT32 or HFS+) data partition.

---

### Post by markp1989 on 2011-03-24
> **Chronon said:**
> What kind of iPod is it?  Does Apple's firmware boot?

I'm mostly familiar with 1g through 5.5g iPods (including Mini 1g/2g and Nano 1g/2g): The MBR should list a raw partition and a (FAT32 or HFS+) data partition.

The iPod is working fine, I just can't update the music :S 

It is a Nano 4th Generation 8gb Black

---

### Post by Chronon on 2011-03-24
Ah.  I have no experience with this model.  What I was talking about only applies to the PortalPlayer based iPods, as far as I know.

I know that a damaged file system can cause volumes to be mounted as read-only.  If this isn't the case for you then there must be another cause.  Unfortunately, I don't have enough experience with this device to imagine other causes for this behavior.

EDIT:
It would be good to verify that the cable and USB port are functioning properly.  It seems like a flaky connection *could* result in the partition being mounted as read-only.

---

### Post by markp1989 on 2011-03-25
> **Chronon said:**
> 
EDIT:
It would be good to verify that the cable and USB port are functioning properly.  It seems like a flaky connection *could* result in the partition being mounted as read-only.

That makes sense, the ipod was connected via a usb hub.

when I go on the pc later I will try it without the hub to see if it makes any difference

---

