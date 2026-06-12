---
title: "weird! ipod becomes readonly when viewed in desktop"
date: 2008-05-30
forum: Multimedia Software
---

### Post by sonichedgehog on 2008-05-30
I have a pig of a problem with this “ipoo”. It mounts (or so it says) as read/write, it’s visible in gtkpod, I can play music from it, but in fact I can’t write to it from gtkpod. On investigation, I find that there is only 1 way I can ever write to it- “umount”, mount manually as root (although I could probably do this as user, just getting into a muddle with my uid’s & gid’s, I’m 1000 & group is 100, suggestions most welcome)  then- this is the important bit- cp to it, or rm, or mkdir, or whatever you want, only from console. As soon as it’s accessed from desktop (KDE in my case) which happens automatically it says it’s readonly filesystem and you have to umount and mount from console. It doesn't matter if you close the window, just viewing it in desktop makes it inaccessible until it's remounted manually.

Here’s some code, if it gives any clues:

```
# mount 
...blah blah blah...
/dev/sdf2 on /media/IPOD type vfat (rw,nosuid,nodev,noatime,uhelper=hal,flush,uid=1000,utf8,shortname=lower) 
```

```
# cp test_graphic.cdr /home/ipod 
cp: cannot create regular file `/home/ipod/test_graphic.cdr': Read-only file system 
```

mounted with
```
# mount -t vfat /dev/sdf2 /home/ipod 
```

then mount showed
```
/dev/sdf2 on /home/ipod type vfat (rw) 
```

and I was able to get into the file system from console, ie write and remove files, including adding to directories that were already there.

```
# file -s /dev/sdf1 
/dev/sdf1: data 

# file -s /dev/sdf 
/dev/sdf: x86 boot sector 

# /sbin/fdisk -l /dev/sdf 

Disk /dev/sdf: 4095 MB, 4095737344 bytes 
255 heads, 63 sectors/track, 497 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x20202020 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdf1   *           1           5       40131    0  Empty 
/dev/sdf2   *           6         497     3951990    b  W95 FAT32 
```

I should confess I'm a Debian user but we're related :) and I'm finding this forum very helpful. I also want to prove to my family that you don't need MS to do the essentials like running your ipod, so honour is at stake. Hope you can help me out here! Cheers.

---

