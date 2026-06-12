---
title: "rsync to NAS results in 'failed to set times'"
date: 2012-02-13
forum: Networking &amp; Wireless
---

### Post by _sebastian_ on 2012-02-13
Hi all,

I want to use rsync to copy my local Pitures to my NAS.

The NAS is a QNAP and the destination is mounted via NFS.

```
rsync -r -t -v --progress --delete -l -D --partial -b -i -s --backup-dir=/home/seb/.chk_deleted_pictures/ /home/seb/Pictures/ /nas/pictures
```

It all goes well but I receive plenty of 
```
rsync: failed to set times on "/nas/pictures/2010/07/19": Operation not permitted (1)
rsync: failed to set times on "/nas/pictures/2010/07/25": Operation not permitted (1)
rsync: failed to set times on "/nas/pictures/2010/07/29": Operation not permitted (1)
rsync: failed to set times on "/nas/pictures/2010/07/31": Operation not permitted (1)
rsync: failed to set times on "/nas/pictures/2010/08/07": Operation not permitted (1)
rsync: failed to set times on "/nas/pictures/2010/08/08": Operation not permitted (1)
rsync: failed to set times on "/nas/pictures/2010/08/09": Operation not permitted (1)
rsync: failed to set times on "/nas/pictures/2010/08/10": Operation not permitted (1)

```

I gues the user thats running the rsync has not sufficient rights to set/change times on the NAS.

How can I check where this proces fails? 
How can I get the time to be updated?

Thanks,

Sebastian

PS: found [this thread]("http://http://ubuntuforums.org/showthread.php?t=1217797&highlight=rsync%3A+failed+set+times") with not too much help

---

### Post by Zimmer on 2012-02-13
[http://www.mikerubel.org/computers/rsync_snapshots/#Rsync](http://www.mikerubel.org/computers/rsync_snapshots/#Rsync)
Do not know the answer but have the above link in my bookmarks ..
This article may give you some pointers and hints on the concern with the timestamps in NAS ....

---

### Post by Zimmer on 2012-02-13
-O, --omit-dir-times
              This tells rsync to omit directories when it is preserving modi&#8208;
              fication times (see --times).  If NFS is sharing the directories
              on the receiving side, it is a good idea to use -O.  This option
              is inferred if you use --backup without --backup-dir.

Looks possible this might help, despite the fact that backup-dir is supposed to 'infer' it... maybe it does not infer it enough ? :)
I have no way of testing this, BTW ..

---

