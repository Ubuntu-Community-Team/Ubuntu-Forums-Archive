---
title: "[SOLVED] No Music-No Usb Mounts- No video"
date: 2008-07-24
forum: Multimedia Software
---

### Post by mattylight on 2008-07-24
So I have just installed Ubuntu on my Acer Aspire One, and I am trying to get my music situation under control. I have an WD mybook 160G with wma music on it and I want to transfer some of it onto this notebook. The computer will not mount the external HD at all. So I put a bunch of music on a usb stick, and the ubuntu wouldn't mount that either. So I took a 16G SDHC card and filled it with music. The computer will see the card, and I can try to play the songs in rythmbox, but they don't play. Then I used soundConverter to change them into OGG, and transfered them into my music folder. Still couldn't import them into rythmbox. So it looks like I have 2 major problems:
1. Can't mount any external storage devices. 
2. Can't import music into the music players. 

I tried searching, but really came up short, and I don't really know where to begin troubleshooting. Thanks in advance. 

Matt

---

### Post by cariboo on 2008-07-25
If you could post the output of:

```
sudo fdisk -l
```

With your devices connected. You will have to do this in a Applications-->Accessories-->Terminal. Post the output in your next post, so that we can help you solve this problem.

Jim

---

### Post by mattylight on 2008-07-25
Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7d8b185

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         933     7494291   83  Linux
/dev/sda2             934         981      385560    5  Extended
/dev/sda5             934         981      385528+  82  Linux swap / Solaris

Disk /dev/sdb: 2000 MB, 2000682496 bytes
64 heads, 63 sectors/track, 969 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         969     1953439+   6  FAT16

Disk /dev/mmcblk0: 16.2 GB, 16240345088 bytes
255 heads, 63 sectors/track, 1974 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1        1975    15855616    c  W95 FAT32 (LBA)

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14593   117218241    c  W95 FAT32 (LBA)

when I type the code from the previous post, this is what comes up. Hope this helps, It looks like sometimes when the computer is booted up with the devices in Ubuntu will mount the External HD and sometimes not. The USB stick is not showing this time, but the mybook is. Thanks.
Matt

---

### Post by lordadi on 2008-07-25
Hi,

If the issue is that your Ubuntu sees the external disks but does not mount them, then maybe this will help. Right click on a panel > Add to panel > Disk mounter. After that see how many disks it shows. If it shows any of your external disks then you can left click on the disk and select mount disk.

If, however, Ubuntu cant even see the disk then I dont know how to help.


Hope it works,

Lordadi.

---

### Post by mattylight on 2008-07-25
I added the disk mounter like you said, and ubuntu sees all the disks, yet this time it has only mounted the mybook and the sd card, but not the usb stick. If I try to mount the USB stick it gives me an error. So the device mounting is intermittent, what I am really concerned with is the ability to use my music files. At the moment I have an SDHC card, and a External HD which both have music files on them. I can look at them, manage their files, but not actually listen to them. I have tried opening the files with rythmbox, but they will not open. So I tried transfering some of them to the SSD hardrive on the laptop itself. They will still not play, then I tried to convert them into OGG, still they do not play. I have sound for webpages, and such, it seems like a software problem to me. Any help would be awesome!
Matt

---

### Post by mattylight on 2008-07-25
[http://www.aspireoneuser.com/forum/viewtopic.php?f=5&t=164&st=0&sk=t&sd=a&start=60](http://www.aspireoneuser.com/forum/viewtopic.php?f=5&t=164&st=0&sk=t&sd=a&start=60)

That is where the answer to the USB situation can be found, all the music and video stuff was fixed from the generic media/video guide found here. If anyone has similiar troubles, pm me.  
Matt

---

