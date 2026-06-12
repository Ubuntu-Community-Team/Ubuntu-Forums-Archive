---
title: "Mplayer doesn't see ntfs partitions in gutsy"
date: 2007-12-18
forum: Multimedia &amp; Video
---

### Post by konata on 2007-12-18
Hi there, I'm still new to Ubuntu here so still not very familiar with it. The problem I have is with mplayer.

I've installed Gutsy and it sees my ntfs partitions fine and VLC is able to play files from my ntfs partitions.

The problem I'm having with mplayer is that when I try to open a file with it, I can only see my linux partitions, whereas with VLC I can see my ntfs partitions. 

As a result I cannot play files from the ntfs partitions with mplayer, while I can with VLC.

How would I be able to make it so that mplayer can see the ntfs partitions?

Thanks in advance.

---

### Post by konata on 2007-12-19
Just tried some other applications like Kaffeine, and also noticed that I am unable to see my ntfs partitions.

Why are some applications able to see my ntfs partitions (like VLC) while others can't? Is there anything that I can do so I will be able to?

Thanks alot.

---

### Post by taurus on 2007-12-19
How do you mount your ntfs partition?  Do you mount it with ntfs or ntfs-3g driver?

Post the outputs of these commands from a terminal.

```
sudo fdisk -l
cat /etc/fstab
mount
```

---

### Post by konata on 2007-12-19
I'm actually using version 7.10 Gutsy Gibbon, and when I installed it, it automatically mounted my ntfs drives.

I'll try what you suggested when I'm on my home machine and post what I get with that command.

Thanks!

---

### Post by konata on 2007-12-20
Ok, here's what i get from the sudo fdisk -l

daniel@wyvern:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6159f6e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36481   293033601    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77484302

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/hda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6ce05761

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7175    57633156    7  HPFS/NTFS
/dev/hda2            7176       48641   333075645    f  W95 Ext'd (LBA)
/dev/hda5            7176       42761   285844513+   7  HPFS/NTFS
/dev/hda6           42762       44463    13671283+  83  Linux
/dev/hda7           44464       48519    32579788+  83  Linux
/dev/hda8           48520       48641      979933+  82  Linux swap / Solaris

---

### Post by konata on 2007-12-20
Just posting to say that I've figured out why I couldn't see the ntfs drives. It was hidden in a link called "Storage media" :)

---

