---
title: "DVDs written in vista refuse to mount"
date: 2008-01-26
forum: Multimedia &amp; Video
---

### Post by jordoex on 2008-01-26
My brother burnt a couple of dvds a while back using the default vista burning software(udf), but I can't read it in ubuntu. 

Does anyone know if there's any codecs/drivers/etc to be able to mount these disks?  When I try to mount it, it just gives me:
> 
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

and dmesg|tail gives:
>  
UDF-fs: No VRS found
 Unable to identify CD-ROM format.


I've tried changing the line in fstab to auto and all of the other basic stuff.  It's not the drive.  Also, "dares", a tool I found in the repos seemed to work, but the output files are kinda messed.  While it did detect the right amount of videos, it didn't parse them properly.

I don't want to have to reboot into windows just to watch a couple videos...

---

### Post by leo_rockway on 2008-01-26
vista's burned stuff uses the udf file system.

check out this thread, you might want to bump it: [http://ubuntuforums.org/showthread.php?t=512782](http://ubuntuforums.org/showthread.php?t=512782)

take a look at this too: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/44233](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/44233)

---

### Post by jordoex on 2008-01-26
Nope, those don't work...
found this in a fedora bug report though:
> These are probably formatted as UDF version 2.50, and not supported in Linux...

I also found this article, which gave a nice insight:
[http://www.groklaw.net/articlebasic.php?story=20070422083715451](http://www.groklaw.net/articlebasic.php?story=20070422083715451)

Although I still should ask exactly how my brother burned those disks, I'll at least remind him to never use the default burning options in vista again. Or at least after vista's service pack 4, where they change the kernel to a bsd-variant.

---

