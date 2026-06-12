---
title: "windows partition not detected"
date: 2011-02-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jprateek on 2011-02-23
I m fairly new to linux environment. Recently I upgraded to ubuntu 11.04 using online upgrade. then i was facing problem with the nvidia driver so I installed xorg 1.99 using recovery mode. Now it is booting but grub is not showing win7 even after "*sudo update-grub" *and even the partition in which windows was there is not detected. please help me out...

---

### Post by Kirboosy on 2011-02-23
Make sure the "Os-prober" package is installed via Synaptic Package Manager

If it is not installed go ahead and install it then rerun
```
sudo update-grub
```

---

### Post by jprateek on 2011-02-23
Yeah I have checked it is installed already...

---

### Post by Kirboosy on 2011-02-23
What version of Windows is it?

Also can you post the output of ```
sudo fdisk -l
```We can try to manually add Windows to GRUB


Oh by the way...[COLOR=Red]Welcome to the forums! :)[/COLOR]

---

### Post by jprateek on 2011-02-23
[B]Here is the output
[/B]

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b2209

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12450   100004593+   7  HPFS/NTFS
/dev/sda2           12451       22904    83971755    7  HPFS/NTFS
/dev/sda3           22905       33360    83987820    7  HPFS/NTFS
/dev/sda4           33361       38914    44602368   83  Linux

now plz tell me what to do....

---

### Post by cariboo on 2011-02-23
I'd suggest you use your install dvd to repair you Windows boot, and then run run a disk check on you main windows partition, as grub is probably not detecting it becuase of a dirty shut down.

If you don't have an install dvd, you can get a rescue disk [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

---

### Post by jprateek on 2011-02-24
Is there any way else...

---

### Post by Kirboosy on 2011-02-24
cariboo907 is right. I didn't even think about checking the integrity of your windows partition.

---

### Post by donniezazen on 2011-02-24
Non of my partitions are detected by gparted it says a long unallocated space.

> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612       14593    96244705+   5  Extended
/dev/sda5            2612        3219     4882432   83  Linux
/dev/sda6            3220        3584     2928640   82  Linux swap / Solaris
/dev/sda7            4557       14594    80621568   83  Linux
/dev/sda8            3584        4556     7809024   83  Linux

Partition table entries are not in disk order


---

### Post by jprateek on 2011-02-25
yeah that was right it worked.....
thanks cariboo.....

PS: @Soham try windows startup repair and then try system restore. I guess this will work out. In my case it did....

---

### Post by cariboo on 2011-02-25
@soham_1207,

Are you running a full SATA system, because with my previous motherboard, none of the SATA drives were detected. Setting the boot order in the BIOS seemed to help, until the board went defective.

---

