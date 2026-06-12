---
title: "Problem Mounting a windows burned data cd"
date: 2008-02-25
forum: Multimedia &amp; Video
---

### Post by speedjunkie on 2008-02-25
Ok, I recently deleted my windows partion and because of that i burned all my songs and videos onto 4 cds using windows default software.  Now when I try to mount them in ubuntu I am getting an error saying "Invalid mount option when attempting to mount the volume 'UDF Volume'."  I changed my fstab to read
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4bb1d7bf-724c-4930-9f06-ba759d081fb7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=8e241ad9-cb0a-420a-856a-a74aa5d25b72 none            swap    sw              0       0
/dev/hda        /media/cdrom0   auto user,noauto,exec 0       0
```
but it didnt changed anything.  I then changed it to this
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4bb1d7bf-724c-4930-9f06-ba759d081fb7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=8e241ad9-cb0a-420a-856a-a74aa5d25b72 none            swap    sw              0       0
/dev/hda        /media/cdrom0   UDF user,noauto,exec 0       0
```
and got a new error message saying "The volume 'UDF Volume' uses the file system which is not supported by your system."

So does this mean I can not get my music and videos off of my 4 cds without getting on a windows machine?  Anyone think they can help?

---

### Post by gsmanners on 2008-02-25
Try "udf,iso9660" instead of just "udf".

And instead of "user,noauto,exec" try "user,noauto,exec,utf8".

---

### Post by speedjunkie on 2008-02-25
no dice:(

my fstab now looks like this
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4bb1d7bf-724c-4930-9f06-ba759d081fb7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=8e241ad9-cb0a-420a-856a-a74aa5d25b72 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

is there anyway to mount this using wine or something like that?

---

### Post by speedjunkie on 2008-02-25
so I tried mounting it using terminal and it said it was write protected (i am guessing thats write as it is a cd-r) but it gives me this message 
```
wrong fs type, bad option, bad superblock on /dev/hda,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

then i do "dmesg" and get this
```
[  637.499772] UDF-fs: No fileset found
[  637.615888] Unable to identify CD-ROM format.
[  659.744640] UDF-fs: No fileset found
[  659.860942] Unable to identify CD-ROM format.
[  719.322671] UDF-fs: No fileset found
[  719.511037] Unable to identify CD-ROM format.
[  732.702936] UDF-fs: No fileset found
[  732.818857] Unable to identify CD-ROM format.
[  995.571765] UDF-fs: No fileset found
[ 1013.371840] UDF-fs: No fileset found
[ 1013.488309] Unable to identify CD-ROM format.
[ 1096.025818] UDF-fs: No VRS found
[ 1096.114827] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1096.193036] ISOFS: changing to secondary root
[ 1128.868006] UDF-fs: No VRS found
[ 1128.956808] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1129.016159] ISOFS: changing to secondary root
[ 1247.109723] UDF-fs: No fileset found
[ 1247.297567] Unable to identify CD-ROM format.
[ 1296.951073] UDF-fs: No fileset found
[ 1297.067178] Unable to identify CD-ROM format.
[ 1450.032127] UDF-fs: No fileset found
[ 1450.148089] Unable to identify CD-ROM format.

```

anyone have any ideas?

---

### Post by speedjunkie on 2008-02-25
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4bb1d7bf-724c-4930-9f06-ba759d081fb7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=8e241ad9-cb0a-420a-856a-a74aa5d25b72 none            swap    sw              0       0
/dev/hda        /media/cdrom0   auto  defaults 0 0
```

thats what it looks like now and when i try to mount the drive it gives me
> You are not privileged to mount the volume 'UDF Volume'

ideas?

---

### Post by toa on 2008-02-25
> **speedjunkie said:**
> ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4bb1d7bf-724c-4930-9f06-ba759d081fb7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=8e241ad9-cb0a-420a-856a-a74aa5d25b72 none            swap    sw              0       0
/dev/hda        /media/cdrom0   auto  defaults 0 0
```

thats what it looks like now and when i try to mount the drive it gives me


ideas?

How about  'sudo' before the mount command in the terminal.

---

### Post by speedjunkie on 2008-02-26
no dice....this is kinda discouraging

---

### Post by speedjunkie on 2008-02-26
well i have come to the conclusion that there is no way to mount these cds seeing as they were burned on vista making them a version of udf that linux cant read.  oh well, now to copy them to my friends computer tommorow and try to burn them from xp and see if that works

---

### Post by Eddie Wilson on 2008-02-26
Were the cd's finalized when they were burned in Windows Vista? I've had problems with linux not being able to read cd's that were not finalized when written by a windows system.

Eddie

---

### Post by speedjunkie on 2008-02-26
vista finalizes every cd before they are ejected correct?  if so then they were each finalized

---

### Post by speedjunkie on 2008-02-26
Well I gave up on trying to mount the vista burned cds...I took them to my roommates vista computer, copied them to his hd, burned a data disc using roxio and made sure it didnt made the file system a udf file system.  I went to mount the cd in on ubuntu and it mounted no problem.  Now to figure out what i have to do to get dvds to play

---

### Post by SonicSteve on 2008-02-27
Hi guys,
I think this problem is happening because windows vista writes DVD's using UDF 2.5 iso-13346. There are patches on the net;
[http://sourceforge.net/tracker/index.php?func=detail&aid=1671912&group_id=295&atid=300295](http://sourceforge.net/tracker/index.php?func=detail&aid=1671912&group_id=295&atid=300295)

However these are very much untested. You'll need to create a custom kernel patching it with the version of this patch for your Kernel version. I've been suggesting for some time that the sourceforge patch listed above be tested by some capable Ubuntu developers. Then add it into the kernel.
I know it's far more involved than that, but we need to fix this issue.

This problem of people burning DVD's with Vista and then trying to read them on Ubuntu Computers is happening more and more.

A while back I added this request to the ubuntu idea pool.
[http://ubuntuforums.org/showthread.php?t=591762](http://ubuntuforums.org/showthread.php?t=591762)

---

