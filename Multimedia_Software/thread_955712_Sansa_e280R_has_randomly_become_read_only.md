---
title: "Sansa e280R has randomly become read only"
date: 2008-10-22
forum: Multimedia Software
---

### Post by grrrlshapedthing on 2008-10-22
I am on a dual boot mint ubuntu computer and randomly recently my Sansa E280R which i have faithfully used for the past year has become read only  I can do anything to change it.. anyone know why this is or what might have caused it or more importantly how I can fix it??? :confused:

---

### Post by prshah on 2008-10-22
> **grrrlshapedthing said:**
> 
recently my Sansa E280R has become read only  I can do anything to change it.. 

Can you plug it in, open a terminal (Applications-Accessories-Terminal) and post the output of the following command?```
sleep 5 && dmesg | tail
lsusb
```

---

### Post by grrrlshapedthing on 2008-10-22
[73482.578417] FAT: Directory bread(block 30638) failed
[73482.578692] FAT: Directory bread(block 30639) failed
[73482.579007] FAT: Directory bread(block 8955536) failed
[73482.579289] FAT: Directory bread(block 8955537) failed
[73482.579574] FAT: Directory bread(block 8955538) failed
[73482.579851] FAT: Directory bread(block 8955539) failed
[73482.580163] FAT: Directory bread(block 8955540) failed
[73482.580443] FAT: Directory bread(block 8955541) failed
[73482.580724] FAT: Directory bread(block 8955542) failed
[73482.581004] FAT: Directory bread(block 8955543) failed
brooklynne@brooklynne-desktop /media/SD PLAYER__ $ lsusb
Bus 005 Device 011: ID 0781:7441 SanDisk Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 046d:c018 Logitech, Inc. 
Bus 001 Device 004: ID 03f0:0324 Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000

---

### Post by prshah on 2008-10-23
> **grrrlshapedthing said:**
> [73482.578417]
[73482.578692] FAT: Directory bread(block 30639) failed
[73482.579007] FAT: Directory bread(block 8955536) failed


Looks like there's some logical damage (may also be physical, but rare); let's eliminate filesystem problems first;

Plug in the device, wait for it to settle, unmount the device (Right click icon, unmount).

Then open a terminal (Applications-Accessories-Terminal) and give the command ```
sudo fsck -a /dev/sdXY
``` (Replace sdXY with the correct device ID for your Sansa player). If you don't know the correct id, give the below command from the terminal while your Sansa is plugged in```
sudo fdisk -l
```

IMPORTANT NOTE: There is a (small) chance that the above fsck command can cause data loss. You should copy anything important off the drive onto your hard disk before you proceed.

---

### Post by grrrlshapedthing on 2008-10-24
thanks will give it a try...

> MPORTANT NOTE: There is a (small) chance that the above fsck command can cause data loss. You should copy anything important off the drive onto your hard disk before you proceed.

nothing important wich is good cause I can't copy anything off or onto it!

---

### Post by grrrlshapedthing on 2008-10-24
okay tried sudo fdisk -l and this is what it gave me

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007c407

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       28846   231705463+  83  Linux
/dev/sda2           28847       38913    80863177+   5  Extended
/dev/sda5           38750       38913     1317298+  82  Linux swap / Solaris
/dev/sda6           28847       38585    78228454+  83  Linux
/dev/sda7           38586       38749     1317298+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdd: 8021 MB, 8021606400 bytes
61 heads, 45 sectors/track, 5707 cylinders
Units = cylinders of 2745 * 512 = 1405440 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        5708     7833300    b  W95 FAT32

which one is my sansa?

ETA: ahh i used some scientific methods of unplugging my sansa and doing fdisk thingy and saw what one disapeard! smart i haz them!

---

### Post by grrrlshapedthing on 2008-10-24
okay ran fsck command and this is what i got

fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdd
/dev/sdd: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by prshah on 2008-10-24
> **grrrlshapedthing said:**
> 
fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdd
/dev/sdd: 

Wrong device /dev/sdd; use ```
sudo fsck -a /dev/sdd1
```

---

### Post by standardhuman on 2008-10-24
I am in the same boat. Nice and corrupted file system, read-only, etc. Following along with the instructions from this thread, fsck runs through and renames a ton of bad filenames, but then seems to hang on one that doesn't seem particularly different than any of the previous ones. 
Then it outputs: 

"Too many files need repair."

I almost laughed when I read this, but what does it mean in terms of further options? Thanks for all your help prshah!

---

### Post by grrrlshapedthing on 2008-10-24
THAT SOOOOOOOOOO WORKED!!!!!!!! WOOOOOOO WOOOOOOOOO WOOOOOOOOOO

Just cause I'm curious any reason how that happened.. I mean what made me notice it was one day I could listen to some songs the next it was ignoring half of them....

---

### Post by prshah on 2008-10-24
> **standardhuman said:**
> 
"Too many files need repair."


You should copy everything that you can off the device, and format it (recreate file system- on the device only!). Then copy back everything onto the new, now-blank player.

On a normal FAT32 storage device, these commands  will do the job:```
sudo umount /dev/sdb1
sudo mkfs.vfat /dev/sdb1
``` but in the specific case of this player, while it will create a fresh, blank filesystem, I don't know if it will affect anything else. (Eg., DRM-protected files, saved settings, etc). So you do this at your own risk. Sorry about that. Remember to replace /dev/sdb1 with the actual device ID.


> **grrrlshapedthing said:**
> THAT WORKED! any reason how that happened.
it was ignoring half of them.

fsck = File System ChecKer. It is used to repair logical damage to the filesystem, such as lost clusters, crosslinked entries, invalid (backup) FAT table, etc.

There are many reasons why such things happen; some common ones are (in order of common occurrence):

a) You unplug the device from the system without first unmounting it (On Windows, you have to use "Safely remove device")

b) Your player runs out of power midway through a song

c) Age. (Of the player!)

d) The player suffers a hard knock _while_ playing a song (only in some cases, don't know if the Sansa falls in this category)

---

