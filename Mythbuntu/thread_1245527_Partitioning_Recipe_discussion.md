---
title: "Partitioning Recipe discussion"
date: 2009-08-20
forum: Mythbuntu
---

### Post by tgm4883 on 2009-08-20
> **klc5555 said:**
> That does seem to be a bit of a flaw with the Mythbuntu 8.04 and later default partitioning scheme: if the unaware user does any of the usual things that one automatically expects to do under /home/<username> on a PC (like saving large files apart from recordings, or working with DVD archiving tools, etc.) that itty-bitty root partition gets maxed out pretty quickly.

I wonder how or whether this default partitioning scheme could be modified in future versions of Mythbuntu without losing the "ease of installation" feature of the installation. Maybe a separate (somewhat bigger) partition for /home ? Even if such a /home partition inadvertently got maxed out, it wouldn't interfere with the OS or PVR functions of the machine.

I've copied this from another thread. Discuss the current default Partitioning recipe below and any suggestions you have.

Modifying the partitioning scheme is pretty easy, it's just a [partman recipe]("http://d-i.alioth.debian.org/svn/debian-installer/installer/doc/devel/partman-auto-recipe.txt"). The one caveat is that we can only have a single recipe (limitation of ubiquity). This means only a single partitioning scheme, so we can't do cool things like multiple drive configuration, only the first drive. If someone wants to post the recipe that they think we should use I will look at it. I don't promise to implement it, but I'll at least look.

Current Partitioning Recipe
```
partman-auto/text/atomic_scheme ::
	
8000 9000 12000 ext3
        $primary{ }
        method{ format }
        format{ }
        use_filesystem{ }
        filesystem{ ext3 }
        mountpoint{ / } .

256 512 1024 linux-swap
        method{ swap }
        format{ } .
	
100 10000 1000000000 xfs
        method{ format }
        format{ }
        use_filesystem{ }
        filesystem{ xfs }
        mountpoint{ /var/lib } .
```

:EDIT:

It has come to my attention that we have reverted to the default Ubuntu partitioning scheme for 9.10, which is a single large EXT4 partition (and 1 small one for swap space).

This discussion should probably change to whether that is an acceptable method or if there is a better one.

---

### Post by klc5555 on 2009-08-20
> **tgm4883 said:**
> Modifying the partitioning scheme is pretty easy, it's just a [partman recipe]("http://d-i.alioth.debian.org/svn/debian-installer/installer/doc/devel/partman-auto-recipe.txt"). The one caveat is that we can only have a single recipe (limitation of ubiquity). This means only a single partitioning scheme, so we can't do cool things like multiple drive configuration, only the first drive. If someone wants to post the recipe that they think we should use I will look at it. I don't promise to implement it, but I'll at least look.


OK, I'll take a first stab at it. (Besides, I've never had the opportunity to try to format a recipe before, and it's fun!  :grin:  ) If the idea is to have a single-disk system that includes a big-honking "/var/lib" for recordings, a minimal "/" and a  "/home" directory that allows the doing of stuff without inadvertently maxing out the root partition and gumming up everything, a recipe might (I hope) look something like this:

12000 12000 24000 ext3
        $primary{ }
        $bootable{ }
        method{ format }
        format{ }
        use_filesystem{ }
        filesystem{ ext3 }
        mountpoint{ / } .

64 512 300% linux-swap
        method{ swap }
        format{ } .

24000 30000  50000 ext3
        method{ format }
        format{ }
        use_filesystem{ }
        filesystem{ ext3 }
        mountpoint{ /home} .


1000 500000 1000000000 xfs
        method{ format }
        format{ }
        use_filesystem{ }
        filesystem{ xfs }
        mountpoint{ /var/lib } .

Which I hope indicates a "/" of around 12G, a "/home" of 24-50G, a swap, and everything else in "/var/lib"

---

### Post by tgm4883 on 2009-08-20
So you are assuming that everyone has a hard disk larger than 40GB that they are installing on for a primary drive?

---

### Post by klc5555 on 2009-08-20
> **tgm4883 said:**
> So you are assuming that everyone has a hard disk larger than 40GB that they are installing on for a primary drive?



Pretty much, since for a backend machine the minimum is currently listed as 20G and the recommended minimum is 80G.

But I take your point, I think, in that frontend-only installations have (at mythbuntu.org) a current listed minimum of 2G (can this still be right in your recipe?) with a recommended minimum of 10+ G. Even though a separate "/var/lib" partition makes less sense for a frontend-only installation, you can only use one recipe.

So, starting from your current recipe, maybe something along these lines would work better than my first try.

6000 9000 12000 ext3
        $primary{ }
        method{ format }
        format{ }
        use_filesystem{ }
        filesystem{ ext3 }
        mountpoint{ / } .

2000 12000 50000 ext3
        method{ format }
        format{ }
        use_filesystem{ }
        filesystem{ ext3 }
        mountpoint{ /home} .

256 512 1024 linux-swap
        method{ swap }
        format{ } .
	
100 10000 1000000000 xfs
        method{ format }
        format{ }
        use_filesystem{ }
        filesystem{ xfs }
        mountpoint{ /var/lib } .

Which might allow a minimum installation close to the current recipe, but still allow for normal work to be done in "/home/<username>" in larger installations without the root partition getting hosed. At least that would be the intent.

---

### Post by jccubs on 2009-08-20
I have a terabyte drive and my machine is for frontend and backend. I have quite a few pictures and home videos saved in my images. I'm actually the reason the other thread was started. Can I use that recipe for my machine? I may add some more pictures and videos in the future, but really have no other use for this machine other than to use it as a DVR. Might possibly put my music on it at some point also if that makes a difference.

---

### Post by tgm4883 on 2009-08-21
It has come to my attention that we have reverted to the default Ubuntu partitioning scheme for 9.10, which is a single large EXT4 partition (and 1 small one for swap space).

This discussion should probably change to whether that is an acceptable method or if there is a better one.

---

### Post by klc5555 on 2009-08-21
> **tgm4883 said:**
> It has come to my attention that we have reverted to the default Ubuntu partitioning scheme for 9.10, which is a single large EXT4 partition (and 1 small one for swap space).

This discussion should probably change to whether that is an acceptable method or if there is a better one.

The default Ubuntu partitioning scheme makes perfect sense to my mind for FE only systems. Which is why I tend to install plain Ubuntu or Xubuntu on machines I want to use FE-only and then add just the mythtv-frontend and dependent packges.

The default scheme also seems to make more sense on multiple-drive BE systems, where the recordings storage drives are all going to be added after installation anyway, so no need for the large /var/lib partition on the boot drive.

But it leaves the original problem from 7.10 and earlier on single-drive backend systems: recordings filling up the root partition and hosing everything. 

It's not elegant, but maybe a solution is to offer two flavors of Mythbuntu, one reciped just for single-drive systems with a backend, and the other flavor reciped with the Ubuntu default for all other types of Mythbuntu systems.


To jccubs:

Your machine is already installed, up, and running. So rather than worrying about partitioning changes, the simplest solution for you, if you think you might wish to store additional photos, videos, music etc. on the machine, might be to create a storage directory for these things under /var/lib (Say, /var/lib/jccubs). Files stored in this directory would naturally be in the large partition and not in your little root partition. The root partition won't get maxed out and lock up on you any longer.

---

### Post by jccubs on 2009-08-24
Totally wiping out my hard drive tonight. Starting from scratch. Was wondering why the only download I could find was 9.04 and the only instruction manual was for 8.10. Is there a download for 8.10 or instructions for 9.04? I just do not want to make any of the same mistakes I made in my previous installation. Any suggestions for partitioning my drivewhen I am asked?

---

