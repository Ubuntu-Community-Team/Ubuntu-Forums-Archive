---
title: "Brasero fails writing CDs"
date: 2010-01-22
forum: Multimedia Software
---

### Post by pveurshout on 2010-01-22
I just tried to burn a Karmic image for a friend, but noticed that when it was done it did not automatically check integrity. Everything seemed to have gone well, though, but something turned out to have gone really bad. When I tried checking the integrity of the burned image, I got the following error:

> The file integrity check could not be performed.
You do not have the required permissions to use this drive.

I re-inserted the CD and it seemed to be able to read everything. Then I ejected and tried on another computer, but it refused to read the CD. Also, I noticed that on the first computer the CD icon had magically reappeared on the desktop - even though the CD had been ejected minutes before!

A while later I also noticed dmesg was flooding with the following:
```

(...)
[12750.427881] VFS: busy inodes on changed media or resized disk sr0
[12752.420099] VFS: busy inodes on changed media or resized disk sr0
[12752.423006] VFS: busy inodes on changed media or resized disk sr0
[12752.426960] VFS: busy inodes on changed media or resized disk sr0
[12754.420976] VFS: busy inodes on changed media or resized disk sr0
[12754.424656] VFS: busy inodes on changed media or resized disk sr0
[12754.428777] VFS: busy inodes on changed media or resized disk sr0
[12756.420004] VFS: busy inodes on changed media or resized disk sr0
(...)

```

I filed a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/511302"), but frankly I'm not sure anymore what is wrong and where to start looking. Does someone know what this could be?

---

