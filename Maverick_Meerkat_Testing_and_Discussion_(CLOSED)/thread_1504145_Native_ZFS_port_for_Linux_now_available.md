---
title: "Native ZFS port for Linux now available"
date: 2010-06-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by pressureman on 2010-06-07
I just stumbled across this on one of the contributing blogs on the Planet OpenSolaris RSS feed - a native port of ZFS for Linux, commissioned by Lawrence Livermore National Laboratories

[http://wiki.github.com/behlendorf/zfs/](http://wiki.github.com/behlendorf/zfs/)

Since it still can't be distributed with or merged into the Linux kernel without violating license(s), this might be an ideal candidate to one day go in Canonical's "partner" repository... Or maybe it's even ok simply to just package it separately from the kernel image, ala linux-restricted-modules.

---

### Post by jfernyhough on 2010-06-07
Bah, just as I'd got btrfs running in a VM...

--edit
Hmm, all of the instructions and sources are for RHL... will those be easy enough to port to Ubuntu/Debian?

---

### Post by ranch hand on 2010-06-07
If you can make a package for RH "alien" should be able to make it go for Debian based stuff.

At least I think so.

---

### Post by pressureman on 2010-06-07
You might want to take a look at their tested platforms before trying it on Ubuntu kernels...

[http://wiki.github.com/behlendorf/zfs/tested-platforms](http://wiki.github.com/behlendorf/zfs/tested-platforms)

---

### Post by jfernyhough on 2010-06-07
I think I'll give it a miss for the minute. :D

I'm in the process of deciding whether to convert my laptop root drive to btrfs now I've successfully done my Maverick VM...

---

### Post by kahumba on 2010-06-07
For desktops, ZFS is only an option for the curious people since Btrfs is around the corner and is rather stable and feature rich.
For servers, in like 3 years Btrfs should be ready even for the enterprise.
Mac also dropped ZFS, so I don't think there's a bright future for ZFS unless Oracle suddenly stops developing Btrfs which I hope won't happen.

---

### Post by zekopeko on 2010-06-07
> **kahumba said:**
> For desktops, ZFS is only an option for the curious people since Btrfs is around the corner and is rather stable and feature rich.
For servers, in like 3 years Btrfs should be ready even for the enterprise.
Mac also dropped ZFS, so I don't think there's a bright future for ZFS unless Oracle suddenly stops developing Btrfs which I hope won't happen.

ZFS has been out and stable far longer then Btrfs. Why wouldn't somebody use a stable filesystem that pretty much has all the features of Btrfs?

---

### Post by Simian Man on 2010-06-07
Considering Oracle started Btrfs and has a lot invested in Linux, I think they will choose to continue developing it rather than continue Sun's ZFS (though arguably more stable at this point).

> **ranch hand said:**
> If you can make a package for RH "alien" should be able to make it go for Debian based stuff.

At least I think so.
Alien fails for a lot of normal packages and you think it will work for a file system?  Good luck with that.

---

### Post by kahumba on 2010-06-08
> **zekopeko said:**
> ZFS has been out and stable far longer then Btrfs. Why wouldn't somebody use a stable filesystem that pretty much has all the features of Btrfs?
Actually not that far longer. And it's not that stable as you might think, you might remember that ZFS actually failed Sun's own recovery test which was like a year or two ago, so it was still a work in progress. You also have to sort out the possible issues introduced when porting over to Linux, so it's not that clean and stable as one might think.

---

### Post by nanog on 2010-06-08
> For desktops, ZFS is only an option for the curious people since Btrfs  is around the corner and is rather stable and feature rich.

To call Brtfs more stable and feature rich than ZFS is  incorrect. Brtfs is not a mature file system while ZFS is a stable file system used in production environments all over the world. If it were not for free software dogma we would all be using it now. And for me, Brtfs will be not be a solution because they still have no plans to support raid5/6.

---

### Post by MacUntu on 2010-06-08
> **nanog said:**
> If it were not for free software dogma we would all be using it now.

Like ZFS is a filesystem designed for desktop environments...

---

### Post by gnomeuser on 2010-06-08
> **kahumba said:**
> For desktops, ZFS is only an option for the curious people since Btrfs is around the corner and is rather stable and feature rich.
For servers, in like 3 years Btrfs should be ready even for the enterprise.
Mac also dropped ZFS, so I don't think there's a bright future for ZFS unless Oracle suddenly stops developing Btrfs which I hope won't happen.

One advantage of having at least read support would be that it would enable migrations (one supposes) at least to a certain extend. It would be important to Oracle as they already have an enterprise Linux offering and it is likely that fuelling two long term isn't going to make sense for them. Offering some form of interoperation would be beneficial to them.

I think one could make a convincing case to Oracle on pure financial gains for them long term in relicening ZFS and the opening the patents they have on the technology to the community.

---

### Post by nanog on 2010-06-08
> **MacUntu said:**
> Like ZFS is a filesystem designed for desktop environments...

no its designed for workstations and servers so running on a desktop should be a snap.  i run it on a laptop (free-bsd) and file server (nexenta) and its the most brilliant file system i have ever used. 

raid-z in linux!!!

---

### Post by nanog on 2010-06-08
posix layer not built yet.  it looks like they are working on it here: [http://kqinfotech.wordpress.com/2009/10/23/hello-world/](http://kqinfotech.wordpress.com/2009/10/23/hello-world/).

mounts with zvol:

[http://wiki.github.com/behlendorf/zfs/example-zvol](http://wiki.github.com/behlendorf/zfs/example-zvol)


snapshots, clones, rollbacks in linux! wooot!

---

### Post by kurros on 2010-06-08
> **nanog said:**
> To call Brtfs more stable and feature rich than ZFS is  incorrect. Brtfs is not a mature file system while ZFS is a stable file system used in production environments all over the world. If it were not for free software dogma we would all be using it now. And for me, Brtfs will be not be a solution because they still have no plans to support raid5/6.

I agree. Btrfs would be a lot more attractive to me if it supported something like RAID-Z (RAID-5/6). I was using the FUSE module for a bit but it's just so unoptimized and slow, and the guy who wrote it got hired by Sun and promptly stopped working on it, yay. So i'm back to FreeBSD ZFS over NFS.

Hopefully this kernel module project matures out for those of us who don't mind a tainted kernel.

Someone from Oracle did say a while back they were interested and investigating making ZFS GPL compatible so I guess we'll see if that ever happens...

---

### Post by tokyovigilante on 2010-07-19
```
ryan@Crackotage:~/zfs$ uname -a
Linux Crackotage 2.6.32-19-generic #28-Ubuntu SMP Thu Apr 1 10:39:41 UTC 2010 x86_64 GNU/Linux
ryan@Crackotage:~/zfs$ sudo zpool upgrade -v
This system is currently running ZFS pool version 26.
```
Seems to be working well in my 10.04 beta VM. Good thing is that the pool version is 26, so while you wait for the ZPL (POSIX layer) to be finished, you can use ZFS-FUSE (which is at 23), and when the ZPL is released, switch to the in-kernel port and upgrade your zpools in place.

---

### Post by nanog on 2010-07-19
> So i'm back to FreeBSD ZFS over NFS.

NFS+ZFS is so very pretty (and smart).

---

### Post by kyleabaker on 2010-07-19
I've been interested in ZFS for a few years now since Apple first became interested in it, but I've never strayed away from the default formats ext3 and ext4. Are there noticeable performance improvements by switching to Brtfs or ZFS? Or are the benefits in filesystem specific features?

Ext4 has been solid for me, but if ZFS ever makes it into the Kernel then I'll likely switch to that.

---

### Post by tokyovigilante on 2010-07-22
Actually, I've just found that you can [use a ZFS ZVOL (virtual block device) with the LLNL ZFS port, and format it with another filesystem]("http://wiki.github.com/behlendorf/zfs/example-zvol"). 

So you could format this ZVOL with ext4, mount it in Ubuntu, and have an in-kernel ZFS protected filesystem, which as far as the system is concerned, is ext4. Once the ZPL is done, migrate your stuff over to the native zpool. Awesome.

I'm going to migrate my NAS to this system this afternoon, will let you know how it goes.

---

