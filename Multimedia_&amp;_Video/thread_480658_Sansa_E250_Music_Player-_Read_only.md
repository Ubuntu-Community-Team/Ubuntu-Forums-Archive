---
title: "Sansa E250 Music Player- Read only?"
date: 2007-06-21
forum: Multimedia &amp; Video
---

### Post by scott_g on 2007-06-21
Hi,

As the title implies, I have a SANSA E250 MP3 player, and am trying to put songs on it in Ubuntu.  However, it mounts as read only, and I cannot seem to mount it in a writable mode :(.

Below is my fdisk readout:

```

scott@scott-ubuntu:~$ fdisk -l

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7752    58605088+   c  W95 FAT32 (LBA)

Disk /dev/sdg: 2010 MB, 2010120192 bytes
62 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 3844 * 512 = 1968128 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1        1011     1942270+   b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 8, 12) logical=(0, 8, 20)
Partition 1 has different physical/logical endings:
     phys=(241, 212, 35) logical=(1010, 42, 12)
Partition 1 does not end on cylinder boundary.
/dev/sdg2            1011        1022       20480   84  OS/2 hidden C: drive
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(241, 212, 36) logical=(1010, 42, 13)
Partition 2 has different physical/logical endings:
     phys=(244, 97, 45) logical=(1021, 20, 52)
Partition 2 does not end on cylinder boundary.

```

Any ideas?

Thanks a lot,
Scott

---

### Post by bsalt on 2007-06-25
I hope this doesn't sound dumb, but did you have your Sansa in MSC mode?

---

### Post by scott_g on 2007-06-25
Yes I did, otherwise it would not show up in the fdisk command, I don't think.

Thanks for the interest,
Scott

---

### Post by Songwind on 2007-06-25
I added a line to fstab including read-write access for my e260.  If you haven't gotten it when I get home from work I will post it.

---

### Post by Songwind on 2007-06-25
Hmm.. I guess I ddin't put any particularly interesting arguments in it:

```
/dev/sdb1       /media/sansa    vfat    user,noauto     0       0
```

---

### Post by scott_g on 2007-07-03
Hi,

First, sorry its taken so long for me to respond; busy times with exams and work and such.

Second, thanks for the suggestions, but I discovered in this thread:  [lnk]http://ubuntuforums.org/showthread.php?p=2957296[/lnk]
that I had a corrupted file on the device, that stopped Ubuntu from mounting the device in a writable mode.

So, on to another question: the device has several folders on it: Music, Photos, Video, etc.  Does anyone know how to tell Rhythmbox to write to the Music Folder?  I'm using Rhythmbox 0.11.0.

Thanks again for the help.
Scott

---

