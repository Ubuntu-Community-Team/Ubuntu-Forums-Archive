---
title: "changing form mythdora to mythbuntu?"
date: 2007-10-22
forum: Mythbuntu
---

### Post by zeltak on 2007-10-22
Hi 

I would love to switch from mythdora (which is also great) to mythbuntu (love ubuntu!!). Question is if there is a way to transfer all my settings, database etc into mythbuntu?

thx alot

Zeltak

---

### Post by tgm4883 on 2007-10-22
you should be able to backup your database and import that.  Also backup your recordings.  That should be all you need, unless you have other settings you want to import.

---

### Post by mungewell on 2007-10-23
> **tgm4883 said:**
> That should be all you need

I note that Mythdora uses LVM by default, not something that I have experience with.

Is it better to stick with LVM and just mount the partion that was '/storage/' (in Mythdora) as '/var/lib/mythtv/' (in Mythbuntu), or reformat the partition as plan ext3?

Maybe an 'expert' could do a quick Mythdora to Mythbuntu upgrade guide.

[I also noted in my playing that mysql will not start unless there is a certain amount of free space available in /var/lib/mysql.]

Cheers,
Simon.

---

### Post by tgm4883 on 2007-10-23
> **mungewell said:**
> I note that Mythdora uses LVM by default, not something that I have experience with.

Is it better to stick with LVM and just mount the partion that was '/storage/' (in Mythdora) as '/var/lib/mythtv/' (in Mythbuntu), or reformat the partition as plan ext3?

Maybe an 'expert' could do a quick Mythdora to Mythbuntu upgrade guide.

[I also noted in my playing that mysql will not start unless there is a certain amount of free space available in /var/lib/mysql.]

Cheers,
Simon.

well whatever you do don't format your recordings partition ext3.  It can be used if you want, but a better solution would be XFS.

You can also use a LVM (not straight out of the Mythbuntu installer though, see the sticky).  IMHO, a better place for recording storage would be outside of /var.  The partitioner has the crazy idea that /var and all subdirectories _**MUST**_ be formated during install :)

---

### Post by mungewell on 2007-10-23
> **tgm4883 said:**
> well whatever you do don't format your recordings partition ext3.

Why? More reasons for a how-to I guess.

The mythdora storage is an ext3 partition within an LVM container....
Simon.

---

### Post by tgm4883 on 2007-10-23
> **mungewell said:**
> Why? More reasons for a how-to I guess.

The mythdora storage is an ext3 partition within an LVM container....
Simon.

from mythtv documentation
> Filesystems

MythTV creates large files, many in excess of 4GB. You must use a 64 or 128 bit filesystem. These will allow you to create large files. Filesystems known to have problems with large files are FAT (all versions), and ReiserFS (versions 3 and 4). The ext3 filesystem can be made to work but requires great care in how you format and mount the volume.

Because MythTV creates very large files, a filesystem that does well at deleting large files is important. Numerous benchmarks show that XFS and JFS do very well at this task. You are strongly encouraged to consider one of these for your MythTV filesystem. JFS is the absolute best at deletion, so you may want to try it if XFS gives you problems. MythTV .20 and above also incorporates a "slow delete" feature, which progressively shrinks the file rather than attempting to delete it all at once, so if you're more comfortable with a filesystem such as ext3 (whose delete performance for large files isn't that good) you may use it rather than one of the known-good high-performance file systems. There are other ramifications to using XFS and JFS - neither offer the opportunity to shrink a filesystem; they may only be expanded.

NOTE: You must not use ReiserFS v3 for your recordings. You will get corrupted recordings if you do.

Because of the size of the MythTV files, it may be useful to plan for future expansion right from the beginning. If your case and power supply have the capacity for additional hard drives, read through the LVM and Advanced Partition Formatting sections for some pointers.

Not saying you can't do it, just saying why would you want to?

---

