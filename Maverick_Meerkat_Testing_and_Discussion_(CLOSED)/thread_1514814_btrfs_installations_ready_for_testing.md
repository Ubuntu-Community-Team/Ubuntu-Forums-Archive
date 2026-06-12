---
title: "btrfs installations ready for testing"
date: 2010-06-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Catharsis on 2010-06-21
SOURCE: [https://lists.ubuntu.com/archives/ubuntu-devel/2010-June/030918.html](https://lists.ubuntu.com/archives/ubuntu-devel/2010-June/030918.html)

With current daily builds of Maverick, you should be able to perform installations with a btrfs root filesystem.  This is still NOT RECOMMENDED FOR PRODUCTION USE and MAY EAT YOUR DATA, but we're making the option available by way of manual partitioning only so that we can experiment with btrfs more easily, contribute fixes to various tools as needed (as we've already done with grub2 in order to at least get this minimal level of support in place), and the like, and hopefully to encourage some more people to get involved in its development.

You cannot yet use btrfs for /boot (although we're working on this), so you'll need to create an ext3 or similar /boot filesystem.  I assume anyone able to use an experimental filesystem can cope with doing that in the installer's manual partitioner.

Please file bugs as you encounter them!  I expect that ext4 will remain the default filesystem for Maverick, but btrfs is doing a lot of things that are interesting for us down the line, so the sooner we can help to iron out problems with it the better.

Cheers,

--
Colin Watson                                       [cjwatson@ubuntu.com]

---

### Post by MacUntu on 2010-06-21
> **Catharsis said:**
> but btrfs is doing a lot of things that are interesting for us down the line

I'm more interested in what btrfs does for me. :P

---

### Post by moviemaniac on 2010-06-21
BTRFS? No thanks, maybe in 5 years when it'll be nearly RC quality*. Until that day comes we'll see dozens of other complete file systems ;)

*anyone reading linux-btrfs should know about the plethora of problems it still has and has had for years. Honestly, I don't want to test a FS which has problems on very, very basic levels like reporting the right size of the file system/free space available. No way.

---

### Post by ranch hand on 2010-06-21
> **moviemaniac said:**
> BTRFS? No thanks, maybe in 5 years when it'll be nearly RC quality*. Until that day comes we'll see dozens of other complete file systems ;)

*anyone reading linux-btrfs should know about the plethora of problems it still has and has had for years. Honestly, I don't want to test a FS which has problems on very, very basic levels like reporting the right size of the file system/free space available. No way.
I am not interested in btrfs either but I can not pass up the opportunity to give you a hard time about it.

If you feel that way about pre RC things, what in flinderation are you doing with 10.10?  It may not take another 5 years but it is not RC quality by long shot.

There, I feel better.

More seriously,  I agree that there are going to be a bunch more mature file systems in the time it takes to finish btrfs.  Basically I just do not see the point of it at all right now.

---

### Post by 23meg on 2010-06-21
Please proceed in [the temporary sticky that I've posted]("http://ubuntuforums.org/showthread.php?t=1514921") (before noticing this thread, and merging will mess up the post order; apologies).

---

