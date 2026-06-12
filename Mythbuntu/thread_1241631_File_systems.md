---
title: "File systems"
date: 2009-08-16
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-08-16
I have a second hard disk in my Mythbuntu box, which I'm using to store movies. 

I have formatted it as ext3, although I notice that the default Mythbuntu installation uses XFS for media storage.

Does this matter? Have I screwed up by formatting it as ext3? If this is less good than XFS, what problems will I notice with ext3 that could have been avoided with XFS?

Thanks
NM

---

### Post by derrick1985 on 2009-08-16
> **NautiusMaximus said:**
> I have a second hard disk in my Mythbuntu box, which I'm using to store movies. 

I have formatted it as ext3, although I notice that the default Mythbuntu installation uses XFS for media storage.

Does this matter? Have I screwed up by formatting it as ext3? If this is less good than XFS, what problems will I notice with ext3 that could have been avoided with XFS?

Thanks
NM

I'm not 100% sure on the file system differences, but I don't think it will matter much. I wouldn't worry about it if I were you. I it was ext2, that would have been another issue.

---

### Post by ian dobson on 2009-08-16
Hi,

You shouldn't see any problems using ext3, my media server (6Tb RAID5 array uses it).

The only problem with ext3 is deleting large files is very slow. But you can enable an option in myth to enable delayed/trimed delete for videos.

Regards
Ian Dobson

---

### Post by NautiusMaximus on 2009-08-17
Splendid. Then I won't worry about it.

---

### Post by klc5555 on 2009-08-17
> **NautiusMaximus said:**
> Splendid. Then I won't worry about it.

In addition to the very zippy deletions with xfs, two other considerations are that 1) ext3 can't be defragged (and ext3 media storage will quickly run up well past 30% fragmented), whereas xfs drives can quite easily be set up to be partially/completely defragged on a daily basis as a cron job. And 2) with 1 T xfs drives (instead of ext3), you never have to put up with a 50 minute fsck at bootup.

Which is why I spent the time to convert all my media storage drives one-by-one to xfs from ext3 a couple of months ago.

---

### Post by NautiusMaximus on 2009-08-17
Oh no! Now I'm worried!

At the moment, I have very little on my second hard drive, so if I'm going to reformat it, I guess now's the time to do it before it fills up.

---

### Post by ian dobson on 2009-08-17
Hi,

Don't be worried, ext3 is the standard file system for linux. 

I've heard of problems with corruption in xfs filesystems which xfs_check/xfs_repair couldn't repair due to insufficient memory (even with 4Gb swap used). With ext3 an fs check does take sometime (on my 3.8Tb array about 2 hours) but I'd rather have a 110% stable system.

There's noth to stop you using ext3 on one drive and xfs on another on the same system.

Maybe have a look here:- [http://www.mythtv.org/wiki/XFS_Filesystem](http://www.mythtv.org/wiki/XFS_Filesystem)

Regards
Ian Dobson

---

### Post by newlinux on 2009-08-17
> **ian dobson said:**
> Hi,

Don't be worried, ext3 is the standard file system for linux. 

I've heard of problems with corruption in xfs filesystems which xfs_check/xfs_repair couldn't repair due to insufficient memory (even with 4Gb swap used). With ext3 an fs check does take sometime (on my 3.8Tb array about 2 hours) but I'd rather have a 110% stable system.

There's noth to stop you using ext3 on one drive and xfs on another on the same system.

Maybe have a look here:- [http://www.mythtv.org/wiki/XFS_Filesystem](http://www.mythtv.org/wiki/XFS_Filesystem)

Regards
Ian Dobson

I too have heard of problems with XFS filesystems on unclean shutdowns. That said, all my recording partitions are in XFS, but my videos, home-movies, dvd collection, movies, and basic backups  of key config files, etc are in EXT3 for peace of mind.

---

### Post by NautiusMaximus on 2009-08-18
Hm. So, if I've understood correctly:

ext3 is more robust than XFS, so I'm less likely to lose data on ext3

XFS is faster than ext3, particularly when moving or deleting large files, and is less likely to suffer problems of fragmentation

I'll be using the second hard drive for storing movies, which are indeed large files, but I don't imagine I'll be moving them around or deleting them all that often, so the speed advantages probably won't make much difference to me.

As for the defragging thing, if I understand correctly, a fragmented file takes longer to read. However, there is usually no point reading a movie file faster than the movie plays. In a worse case scenario and my ext3 drive with movies on gets horribly fragmented, is there a risk that reading the file wouldn't be able to keep up with the speed at which the movie is played?

---

### Post by djurny on 2009-08-18
> **NautiusMaximus said:**
> ext3 is more robust than XFS, so I'm less likely to lose data on ext3
that is a rather blunt conclusion ([http://en.wikipedia.org/wiki/XFS](http://en.wikipedia.org/wiki/XFS)).. if you have powerfailuers, either filesystem is going to cause trouble..
i personally would not base robustness of a fs on the amount of fsck invocations.. 
i've experienced enough fsck.ext3 mishaps (understatement) to come to another conclusion :D

---

### Post by newlinux on 2009-08-18
> **NautiusMaximus said:**
> Hm. So, if I've understood correctly:

ext3 is more robust than XFS, so I'm less likely to lose data on ext3

This is debatable, but I feel more comfortable with ext3 based on my personal experience and that of those that I know.  I once had an unclean shutdown  with a system that had both ext3 and XFS filesystems, and I wasn't able to recover the data from the XFS drive (I wasn't as experienced then, and I probably could have with more work). The ext3 drive was fine. This certainly isn't scientific proof, but that combined with the experience of others makes me put my most valuable files on ext3 and back them up.

> 
XFS is faster than ext3, particularly when moving or deleting large files, and is less likely to suffer problems of fragmentation

Yep, that's my understanding.

> 
I'll be using the second hard drive for storing movies, which are indeed large files, but I don't imagine I'll be moving them around or deleting them all that often, so the speed advantages probably won't make much difference to me.

My reasoning for how my system is setup is exactly the same. although, I backup all my non recording media files nightly, so I guess I could have the primary on XFS and the backup on ext3, but ext3 hasn't caused me problems.

> 
As for the defragging thing, if I understand correctly, a fragmented file takes longer to read. However, there is usually no point reading a movie file faster than the movie plays. In a worse case scenario and my ext3 drive with movies on gets horribly fragmented, is there a risk that reading the file wouldn't be able to keep up with the speed at which the movie is played?
I doubt there is any risk. I suppose it's possible - never happened to anyone I know.

---

