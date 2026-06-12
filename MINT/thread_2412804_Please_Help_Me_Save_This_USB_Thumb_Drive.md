---
title: "Please Help Me Save This USB Thumb Drive"
date: 2019-02-17
forum: MINT
---

### Post by tinker123 on 2019-02-17
I have a 4 GB MicroVault USB stick

I messed it (adding and removing partitions) up trying to get something done.   

Bottom line, it now appears as two devices rather than one when I plug it into my computer.

I would like to get the USB stick back to where it appears as just one device, and is ready to put a bootable ISO image on it.

Attached are screen shots of how the stick appears to my desktop/nautilus, gparted, and the GNOME disk utility.

Any help will be greatly appreciated.

Here is an fdisk ahd lsblk read out:


```


Mint19Cinamon3.8.9> fdisk /dev/sdc

Welcome to fdisk (util-linux 2.31.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.


Command (m for help): p
Disk /dev/sdc: 512 B, 512 bytes, 1 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x032e53a8

Command (m for help): q

Mint19Cinamon3.8.9> lsblk
NAME                MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                   8:0    0 232.9G  0 disk 
&#9492;&#9472;sda1                8:1    0 232.9G  0 part 
  &#9500;&#9472;mint--vg-root   253:0    0   217G  0 lvm  /
  &#9492;&#9472;mint--vg-swap_1 253:1    0    16G  0 lvm  [SWAP]
sdb                   8:16   0 931.5G  0 disk 
&#9492;&#9472;sdb1                8:17   0 931.5G  0 part 
sdc                   8:32   1   3.8G  0 disk 
&#9500;&#9472;sdc1                8:33   1   2.1G  0 part /media/steve/US2
&#9492;&#9472;sdc2                8:34   1   1.7G  0 part /media/steve/casper-rw
sr0                  11:0    1  1024M  0 rom  
Mint19Cinamon3.8.9> 



```

---

### Post by brian_p on 2019-02-17
sudo dd if=/dev/zero of=/dev/sdc count=1000

But double-check that the device is sdc.

---

### Post by tinker123 on 2019-02-17
> **brian_p said:**
> sudo dd if=/dev/zero of=/dev/sdc count=1000

But double-check that the device is sdc.

Thanks for the suggestion.  I tried it.  No change.

---

### Post by QIII on 2019-02-17
Hello!

What was the actual command you issued?  Verbatim.

What is the current output of lsblk?

---

### Post by brian_p on 2019-02-17
> **tinker123 said:**
> Thanks for the suggestion.  I tried it.  No change.

Without "count=1000".

---

### Post by tinker123 on 2019-02-17
> **QIII said:**
> Hello!

What was the actual command you issued?  Verbatim.



```
Mint19Cinamon3.8.9> dd if=/dev/zero of=/dev/sdc count=1000
1000+0 records in
1000+0 records out
512000 bytes (512 kB, 500 KiB) copied, 0.0035136 s, 146 MB/s
Mint19Cinamon3.8.9>
```



> What is the current output of lsblk?



```
Mint19Cinamon3.8.9> lsblk
NAME                MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                   8:0    0 232.9G  0 disk 
&#9492;&#9472;sda1                8:1    0 232.9G  0 part 
  &#9500;&#9472;mint--vg-root   253:0    0   217G  0 lvm  /
  &#9492;&#9472;mint--vg-swap_1 253:1    0    16G  0 lvm  [SWAP]
sdb                   8:16   0 931.5G  0 disk 
&#9492;&#9472;sdb1                8:17   0 931.5G  0 part 
sdc                   8:32   1   3.8G  0 disk 
&#9500;&#9472;sdc1                8:33   1   2.1G  0 part /media/steve/US2
&#9492;&#9472;sdc2                8:34   1   1.7G  0 part /media/steve/casper-rw
sr0                  11:0    1  1024M  0 rom  
Mint19Cinamon3.8.9>
```

---

### Post by tinker123 on 2019-02-17
> **brian_p said:**
> Without "count=1000".

I did this

```
Mint19Cinamon3.8.9> sudo dd if=/dev/zero of=/dev/sdc
dd: writing to '/dev/sdc': No space left on device
16288945+0 records in
16288944+0 records out
8339939328 bytes (8.3 GB, 7.8 GiB) copied, 12.6652 s, 658 MB/s
Mint19Cinamon3.8.9> 
```

No change.  When I plug the USB stick in it is still showing up as two devices.

---

### Post by yancek on 2019-02-17
It's not showing two devices but two partitions on that device.  You are referring to sdc, correct?  If there is no data on it that you want, simply create a new partition table using GParted.  Click the drop down arrow in the upper right of the window and select /dev/sdc (if that is the correct drive?) then click on the Device tab at the top of the GParted window and Click Create Partition Table and make your selection, should be msdos/MBR or GPT.

---

### Post by oldos2er on 2019-02-17
Moved to MINT.

---

### Post by tinker123 on 2019-02-17
> **yancek said:**
> It's not showing two devices but two partitions on that device.  You are referring to sdc, correct?  If there is no data on it that you want, simply create a new partition table using GParted.  Click the drop down arrow in the upper right of the window and select /dev/sdc (if that is the correct drive?) then click on the Device tab at the top of the GParted window and Click Create Partition Table and make your selection, should be msdos/MBR or GPT.

In Nautilus and the desktop it is show up as 2 devices ( see screen shots in first post ).

I tried creating a partition table with GParted, but GParted throws a bunch of "end of file" errors and does nothing.

---

### Post by brian_p on 2019-02-17
> In Nautilus and the desktop it is show up as 2 devices ( see screen shots in first post ).

Post what is seen with

[HTML]sudo cfdisk /dev/sdc[/HTML]

---

### Post by QIII on 2019-02-17
Was this device previously mounted on a Windows machine?

---

### Post by Autodave on 2019-02-17
In gparted, you first need to remove all partitions. Then, create a new partition using the entire disk.

---

### Post by tinker123 on 2019-02-18
**SOLVED.**


My PC has Mint 19 on it.

I burned a live DVD of Mint 19.1 and successfully used the tools mentioned in this thread, while using the live DVD, to fix the USB stick.

Something is wrong with my current Mint 19 installation.

I will move on at some point.

Thanks to everyone who donated their time and effort trying to help.

It is appreciated.

---

