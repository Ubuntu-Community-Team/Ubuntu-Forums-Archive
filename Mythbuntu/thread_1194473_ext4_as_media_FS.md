---
title: "ext4 as media FS?"
date: 2009-06-22
forum: Mythbuntu
---

### Post by MythAaron on 2009-06-22
Has anyone tried it?  If so, how does it perform compared to XFS?

---

### Post by ian dobson on 2009-06-23
Hi,

ext4 is still too new. Only afew months ago there were reports of corruption with large files ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/348836](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/348836)).

Maybe in 6-9months I'll go over to ext4, but for me it's just too young at the moment.

The performance tests I've see up it'll now look good for a video partition (Large file access/creation/Large file delete).

Regards
Ian Dobson

---

### Post by teet on 2009-06-23
I was wondering this as well.  I was considering upgrading to a nice 1.5 TB drive in the near future and so want to make a wise choise in my partition file system.

JFS has served me well for the past 3 years so I guess I'll probably just stick with that.

-teet

---

### Post by MythAaron on 2009-06-23
I'm really tempted to try ext4 even though it's still green.  My dislike of XFS is past green.  :)

---

### Post by LowSky on 2009-06-23
ext4 has worked fine for me. It being too new is an odd argument, but then  again most of the world wont leave Windows XP or NTFS and both are really showing their age.

and that [link]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/348836") well it was an issue during 9.04 Beta testing,and other distro around the same time... the worst issue being corrected for 9.04 while other distros wait for the newer kernel (2.6.30) to address.

EXT4 is meant as a journaling file system an dnot really that important for a media storage, EXT2 would be a better choice I would say.

---

### Post by Jeconti on 2009-06-23
My recordings partition is actually formatted as ext4 at the moment. I'm probably going to change it though. So far I haven't had any real issues with it, but I'm just getting the whole thing up and running. I've only recorded two shows.

---

### Post by Monsieur Gonzalez on 2009-06-24
Been using it since upgrading to Jaunty. So far, it's been a great update. Delete speeds are far better than ext3, and fsck times are much faster. Had a couple of lockups and experienced no data loss. YMMV, of course.

---

### Post by MythAaron on 2009-06-24
How is playback performance?  How does it compare to XFS?

---

### Post by Monsieur Gonzalez on 2009-06-25
I'm sure you'll find more objective comparisons/benchmarks searching Google, but, for me, there's no 'real life' difference. I've not played 1080p content, though, just 720p.

---

### Post by movieman on 2009-06-25
> **LowSky said:**
> EXT4 is meant as a journaling file system an dnot really that important for a media storage, EXT2 would be a better choice I would say.

Ext4 is designed to handle large files more efficiently than ext2 (e.g. delayed allocation to reduce fragmentation), so it should be a pretty good candidate for media storage.

Personally I wouldn't touch it for a system partition with the various bugs we've seen so far (e.g. truncating files to 0 bytes on a power failure), but for recording TV shows it may be worth a look.

---

### Post by MythAaron on 2009-06-29
[Phoronix]("http://www.phoronix.com/scan.php?page=article&item=ext4_btrfs_nilfs2&num=1") released a set of comparisons between EXT4, BTRFS, NILFS2 today.  They also threw XFS and EXT3 into the mix as controls.  The results are interesting and each filesystem has their niches where they shine.  However, EXT4 seems to win on straight large file read and write performance.

---

