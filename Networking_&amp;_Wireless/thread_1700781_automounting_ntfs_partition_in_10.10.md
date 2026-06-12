---
title: "automounting ntfs partition in 10.10"
date: 2011-03-05
forum: Networking &amp; Wireless
---

### Post by Acimer on 2011-03-05
Hi!

I'm running 10.10 and Windows 7 dual boot. I already have lots of music and videos on the Windows partition and I would like to share it with ubuntu partition. I can if I mount it every time manually, but i want the partition to mount automatically so that when I use Amarok for example i don't have to rescan the music files on every startup. 

What should i put in fstab?


```
sudo /sbin/fdisk -l
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x939f2aac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             192         204      101376   82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sda3             205       32506   259460096    7  HPFS/NTFS
/dev/sda4           32507       38914    51465380+   5  Extended
/dev/sda5           32507       38645    49311486   83  Linux
/dev/sda6           38646       38914     2153472   82  Linux swap / Solaris
andrej@Nakama:~$ sudo blkid
/dev/sda1: LABEL="TOSHIBA SYSTEM VOLUME" UUID="5C5AE66B5AE640FE" TYPE="ntfs" 
/dev/sda2: UUID="a7f8a8d7-8794-48f3-8a0f-f9793747c014" TYPE="swap" 
/dev/sda3: LABEL="Windows 7" UUID="862417FE2417F043" TYPE="ntfs" 
/dev/sda5: UUID="6d31a0c2-459f-4889-b97e-8c0f1eae41a2" TYPE="ext4" 
/dev/sda6: UUID="3481333b-eeeb-4a8d-8f15-b6f0d31667a8" TYPE="swap" 

```

```
andrej@Nakama:~$ sudo blkid
/dev/sda1: LABEL="TOSHIBA SYSTEM VOLUME" UUID="5C5AE66B5AE640FE" TYPE="ntfs" 
/dev/sda2: UUID="a7f8a8d7-8794-48f3-8a0f-f9793747c014" TYPE="swap" 
/dev/sda3: LABEL="Windows 7" UUID="862417FE2417F043" TYPE="ntfs" 
/dev/sda5: UUID="6d31a0c2-459f-4889-b97e-8c0f1eae41a2" TYPE="ext4" 
/dev/sda6: UUID="3481333b-eeeb-4a8d-8f15-b6f0d31667a8" TYPE="swap" 

```

```
ls /media
fstab  Windows  Windows 7

```

"Windows" is an empty folder, i guess i can delete it? 

what should the **mount point** be?

in fstab, should i add the line:
```
UUID=862417FE2417F043 **/media/Windows 7** ntfs-3g auto,rw,user 0 0
```  or something else?

thanks

---

### Post by marin123 on 2011-03-05
install ntfs-config, run it and select your partition to automount. you dont need to edit fstab.

```
sudo apt-get install ntfs-config
```

---

### Post by Morbius1 on 2011-03-05
**Create a permanent mount point for the partition to live in:**
```
sudo mkdir /media/Win7
```**Add a line to fstab - one option:**
```
 UUID=862417FE2417F043 /media/Win7 ntfs-3g defaults,uid=1000 0 0
```**After saving fstab run the following command to test for errors and mount the new mount point:**
```
sudo mount -a
```Please note that I am not a fan of mounting a Windows OS partition with write access which is what the above fstab line will do. I prefer read access only:
```
UUID=862417FE2417F043 /media/Win7 ntfs-3g defaults,umask=222,uid=1000 0 0
```But that choice is up to you.

---

### Post by Acimer on 2011-03-05
> **marin123 said:**
> install ntfs-config, run it and select your partition to automount. you dont need to edit fstab.


I was told not to use ntfs-config because it can mess up the mounting partition. 

[QUOTE=Coffeecat] My advice - don't. And I'm not the only one. I agree 100% with Mark Phelps' reasons:

Quote:
Originally Posted by Mark Phelps View Post
If the NTFS partition you intend to mount is an OS partition containing Vista or Win7, I would advise strongly AGAINST mounting it -- unless you mount it read-only.

Mounting a Vista or Win7 OS partition read-write is asking for trouble. One unclean shutdown or journal error and the whole partition is then unbootable. And since you then can't boot into Vista or Win7 to run chkdsk to fix it, you're hosed.
The risk is so great and ntfs-config is such a buggy, poorly-implemented utility that does the most extraordinarily stupid things on occasion that I am doing you a favour by not telling you how to get it going.

If you really must read your Windows C: partition, mount it on an as-needed basis from the Places menu and then dismount it as soon as you can. Even this can lead to trouble. This is not an Ubuntu problem - this is entirely down to Windows.

If, however, you want a shared NTFS data partition to be accessible in both Windows and Ubuntu then that's another matter. If that's what you want and you need help with editing /etc/fstab then I suggest you start another thread but don't think of using ntfs-config, even if someone recommends it. I've seen it do the craziest things. It's a mess.[/QUOTE]

[View Post]("http://ubuntuforums.org/showthread.php?t=1644874")

---

### Post by Morbius1 on 2011-03-05
The very first thing that ntfs-config asks you is if you want to enable write access to NTFS. ntfs-3g has write access by default.

So you have to ask yourself why doesn't ntfs-config know that and what on earth does it do should you answer: yes.

---

### Post by Acimer on 2011-03-05
Thanks, I will try!

>  Please note that I am not a fan of mounting a Windows OS partition with write access which is what the above fstab line will do. I prefer read access only:
```
UUID=862417FE2417F043 /media/Win7 ntfs-3g defaults,umask=222,uid=1000 0 0
```But that choice is up to you.

Why are you a fan of mounting with write access? What are pros and cons of it?

For listening to music/ watching videos from that partition the read-only option is sufficient, right?

---

### Post by Morbius1 on 2011-03-05
I am [COLOR=Blue]**not**[/COLOR] a fan of write access to the Windows OS partition for the same reasons Mark Phelps mentioned in your quote. A umask=222 will turn off write access to that partition.

---

### Post by Acimer on 2011-03-05
> **Morbius1 said:**
> I am [COLOR=Blue]**not**[/COLOR] a fan of write access to the Windows OS partition for the same reasons Mark Phelps mentioned in your quote. A umask=222 will turn off write access to that partition.

Yeah, I accidentally didn't type "not" , sorry! Ok I have it as read-only and it is automounting properly.
Thanks for help!

---

