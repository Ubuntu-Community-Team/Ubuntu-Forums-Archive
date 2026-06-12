---
title: "Any likelihood that maverick meerkat will support trim?"
date: 2010-06-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by josephellengar on 2010-06-08
I've been waiting for Ubuntu to implement the trim() feature for ssds for quite a while now and was wondering if this will happen in MM.  I know that it is supported in the kernel at this point, but will there be OS-level support?

---

### Post by josephellengar on 2010-06-09
> **rossholley said:**
> I've been waiting for Ubuntu to implement the trim() feature for ssds for quite a while now and was wondering if this will happen in MM.  I know that it is supported in the kernel at this point, but will there be OS-level support?

bump

---

### Post by gnomeuser on 2010-06-09
I think you can be certain that this will happen, Ubuntu's Unity project is aimed at deployments on flash (for OEMs to offer instant on internet access). It would make sense for them to work on making this as effecient as possible and trim support is likely to be part of that equation.

---

### Post by josephellengar on 2010-06-09
> **gnomeuser said:**
> I think you can be certain that this will happen, Ubuntu's Unity project is aimed at deployments on flash (for OEMs to offer instant on internet access). It would make sense for them to work on making this as effecient as possible and trim support is likely to be part of that equation.

Oh, thanks.

---

### Post by plun on 2010-06-09
This is rather strange... I bought myself a Intel X25-M G2, 80GB SSD for my laptop.   Excellent performance and it just works.


According to this blueprint Trim should be implemented already and this during Karmic development.

[https://blueprints.launchpad.net/ubuntu/+spec/kernel-karmic-ssd](https://blueprints.launchpad.net/ubuntu/+spec/kernel-karmic-ssd)

Details:
[https://wiki.ubuntu.com/KernelTeam/Specs/KarmicSSD](https://wiki.ubuntu.com/KernelTeam/Specs/KarmicSSD)

Correct or wrong :confused:

--

---

### Post by josephellengar on 2010-06-09
> **plun said:**
> This is rather strange... I bought myself a Intel X25-M G2, 80GB SSD for my laptop.   Excellent performance and it just works.


According to this blueprint Trim should be implemented already and this during Karmic development.

[https://blueprints.launchpad.net/ubuntu/+spec/kernel-karmic-ssd](https://blueprints.launchpad.net/ubuntu/+spec/kernel-karmic-ssd)

Details:
[https://wiki.ubuntu.com/KernelTeam/Specs/KarmicSSD](https://wiki.ubuntu.com/KernelTeam/Specs/KarmicSSD)

Correct or wrong :confused:

--

It never materialized.  I followed the whole thing hoping that it would be implemented during KK or LL.  It wasn't.

---

### Post by plun on 2010-06-09
OK.... found this bug.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/571476](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/571476)

And this Gentoo thread:
[http://forums.gentoo.org/viewtopic-t-812509.html](http://forums.gentoo.org/viewtopic-t-812509.html)

And this U-F thread
[http://ubuntuforums.org/showthread.php?t=1490602](http://ubuntuforums.org/showthread.php?t=1490602)

I dont want to ruin my new disk with above so I wait....

---

### Post by Reiger on 2010-06-09
The trouble with the OCZ drive may refer to the (old?) problem of not supporting SATA NCQ correctly. You'll find a thread in either Lucid or Karmic testing forums about that. [For the life of me I can't remember the nickname of the user who started that thread, V something I think... And describing his avatar won't help you.]

---

### Post by josephellengar on 2010-06-09
> **plun said:**
> OK.... found this bug.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/571476](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/571476)

And this Gentoo thread:
[http://forums.gentoo.org/viewtopic-t-812509.html](http://forums.gentoo.org/viewtopic-t-812509.html)

And this U-F thread
[http://ubuntuforums.org/showthread.php?t=1490602](http://ubuntuforums.org/showthread.php?t=1490602)

I dont want to ruin my new disk with above so I wait....

Well, I don't think that these indicate a likelihood of ruining the drive.  The first is simply the problem that I am complaining about- that we don't have trim.  The second is trying to implement trim in the fs (when it probably isn't implemented in the OS), and the third is trouble installing the utility, not trouble using the utility.  And the utility mentioned is not real trim, it's "fake" trim.
Actually, the utility mentioned in the third thread you linked is very good.  Hdparm comes with a wiper.sh script that seems to do a pretty good job of trimming, but as I said, it's "fake," in that you have to manually pass the command to the drive.  Anyway, it's hard to screw up a drive permanently with the trim() command, as all it does is erase data, so I don't think it could cause anything other than stability problems.  So when it is implemented I will definitely use it and continue my strict backup regimen.

---

### Post by castrojo on 2010-06-09
Didn't TRIM go in in 2.6.33? (And therefore be in 2.6.34 that's in maverick?)

---

### Post by josephellengar on 2010-06-09
> **whiprush said:**
> Didn't TRIM go in in 2.6.33? (And therefore be in 2.6.34 that's in maverick?)

Yes, but it requires OS support in addition to kernel support.

---

### Post by MacUntu on 2010-06-10
[QUOTE=linux-doc/filesystems/ext4]discard/nodiscard:
Controls whether ext4 should issue discard/TRIM commands to the underlying block device when blocks are freed.  This is useful for SSD devices and sparse/thinly-provisioned LUNs, but it is off by default until sufficient testing has been done.[/QUOTE]
In my understanding you should just need to add the 'discard' option to your entries in '/etc/fstab'.

As for the alignment part:
[QUOTE=Lucid release notes]By default, Ubuntu 10.04 LTS aligns partitions on disk to 1 MiB (1048576 bytes) boundaries. This ensures maximum performance on many modern disks, particularly solid state drives but also new "Advanced Format" disks with physical sectors larger than the traditional 512 bytes.[/QUOTE]

AFAIK this goes for the installer only, not for (G)Parted.

**Edit:**

From a fresh Maverick daily install (auto-partitioned):

[[img]http://img.xrmb2.net/947381.jpg[/img]](http://img.xrmb2.net/images/947381.png)

---

### Post by josephellengar on 2010-06-10
> **MacUntu said:**
> 

In my understanding you should just need to add the 'discard' option to your entries in '/etc/fstab'.



So if my entry is:

```

UUID=c21bc2a3-4e3c-44bb-8d01-a021624afc54 /               ext4    errors=remount-ro 0       1

```

I would just change it to:

```

UUID=c21bc2a3-4e3c-44bb-8d01-a021624afc54 /               ext4    errors=remount-ro,discard 0       1 

```

It will work in MM?  Can I do the same thing in LL and KK or is this new?  I've been looking for a way to do this in those releases too but my other threads ended with a consensus that trim was impossible in those releases.

---

### Post by MacUntu on 2010-06-10
The discard option was introduced with the 2.6.33 kernel, so if you can run this kernel (or later) on those releases it *should* work. Please note: I currently don't have a SSD so I'm just guessing. ;)

---

### Post by plun on 2010-06-10
> **rossholley said:**
> 

It will work in MM?  Can I do the same thing in LL and KK or is this new?  I've been looking for a way to do this in those releases too but my other threads ended with a consensus that trim was impossible in those releases.

Ok found this guide about Trim and other tweaks. Up and running !

[http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/](http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/)

From this thread:
[http://swiss.ubuntuforums.org/showthread.php?t=1432194](http://swiss.ubuntuforums.org/showthread.php?t=1432194)

Journaling disabled and the changed fstab to this:

```
# / was on /dev/sda1 during installation
UUID=cce29c05-0460-47f8-a591-171a60947546 /               ext4	noatime,discard,defaults      0       1
```


(I first tested the wiper.sh script but its broken for me, I/O error.)

---

### Post by josephellengar on 2010-06-10
> **plun said:**
> Ok found this guide about Trim and other tweaks. Up and running !

[http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/](http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/)

From this thread:
[http://swiss.ubuntuforums.org/showthread.php?t=1432194](http://swiss.ubuntuforums.org/showthread.php?t=1432194)

Journaling disabled and the changed fstab to this:

```
# / was on /dev/sda1 during installation
UUID=cce29c05-0460-47f8-a591-171a60947546 /               ext4	noatime,discard,defaults      0       1
```


(I first tested the wiper.sh script but its broken for me, I/O error.)

What kernel does this require?  Can I do it in KK or LL?  I don't want to use a development release but I want trim to work so badly.  The wiper.sh script does work, but only intermittently and I am concerned every time I see the "THIS WILL DAMAGE YOUR DATA" message or whatever it says :shock:

EDIT: And how do you disable journaling?  That's not required is it?  I think that they just do that to prolong the life of the drive.

---

### Post by plun on 2010-06-10
> **rossholley said:**
> What kernel does this require?  Can I do it in KK or LL?  I don't want to use a development release but I want trim to work so badly.  The wiper.sh script does work, but only intermittently and I am concerned every time I see the "THIS WILL DAMAGE YOUR DATA" message or whatever it says :shock:

EDIT: And how do you disable journaling?  That's not required is it?  I think that they just do that to prolong the life of the drive.

I am running Maverick and the 2.6.35-2 kernel (RC2 based)

With Lucid you can use a Ubuntu Mainline kernel.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)


Just read the guide how to disable journaling, according to the author this is preferred.

Bootchart:
[[img]http://ubuntu-pics.de/thumb/80892/plun_laptop_maverick_20100610_1_I36xzv.png[/img]](http://ubuntu-pics.de/bild/80892/plun_laptop_maverick_20100610_1_I36xzv.png)  

Disk utility:
[[img]http://ubuntu-pics.de/thumb/80895/screenshot_80_gb_solid_state_disk__ata_intel_ssdsa2m080g2gc______benchmark_65nxJ8.png[/img]](http://ubuntu-pics.de/bild/80895/screenshot_80_gb_solid_state_disk__ata_intel_ssdsa2m080g2gc______benchmark_65nxJ8.png)

---

### Post by josephellengar on 2010-06-10
> **plun said:**
> I am running Maverick and the 2.6.35-2 kernel (RC2 based)

With Lucid you can use a Ubuntu Mainline kernel.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)


Just read the guide how to disable journaling, according to the author this is preferred.

Bootchart:
[[img]http://ubuntu-pics.de/thumb/80892/plun_laptop_maverick_20100610_1_I36xzv.png[/img]](http://ubuntu-pics.de/bild/80892/plun_laptop_maverick_20100610_1_I36xzv.png)  

Disk utility:
[[img]http://ubuntu-pics.de/thumb/80895/screenshot_80_gb_solid_state_disk__ata_intel_ssdsa2m080g2gc______benchmark_65nxJ8.png[/img]](http://ubuntu-pics.de/bild/80895/screenshot_80_gb_solid_state_disk__ata_intel_ssdsa2m080g2gc______benchmark_65nxJ8.png)

Ok, thanks.  So I have set up my fstab as follows:

```

# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0

# root filesystem
UUID=098c0e33-2ea8-420a-a7c9-2bcdc9011118 / ext4 errors=remount-ro,discard 0 1

# swap file
UUID=0de4ba0c-7406-4974-a25b-a1d10f68be39 none swap sw 0 0

#storage
/dev/sdb1 /home/ross/storage ntfs-3g auto,user,uid=1000,gid=100,dmask=027,fmask=137,utf8 0 0

#flash drive
/dev/sdc1 /home/ross/flash vfat iocharset=utf8,umask=000,user 0 0

```

The discard is on the root filesystem, which is the only ssd that I have.  I also have installed the file: linux-image-2.2.6.34-020634-generic_2.6.34-020634_amd64 from the link that you supplied.  If I run this kernel with the above fstab, trim should be enabled, correct?  Is there any way to test this?  If it is working then I think that I probably will disable journaling at some point.  Thanks for the help!

---

### Post by plun on 2010-06-10
> **rossholley said:**
>  If I run this kernel with the above fstab, trim should be enabled, correct?  Is there any way to test this?  If it is working then I think that I probably will disable journaling at some point.  Thanks for the help!

Yep... as I understands it but I am just a happy Ubuntu tester...):P

I am also trying to figure out how to test this...:confused:

My laptop feels "snappier" and all read and writes are going fast.

---

### Post by josephellengar on 2010-06-10
> **plun said:**
> Yep... as I understands it but I am just a happy Ubuntu tester...):P

I am also trying to figure out how to test this...:confused:

My laptop feels "snappier" and all read and writes are going fast.

Well, I tried that kernel and it refused to boot KK, so I'm going to stick with what I have for a while.  As I understand it, it can't hurt to send the trim command, so I'll just leave that in.  Anyway, thanks for the help.  Hopefully in an upcoming release they will this all easier.

---

