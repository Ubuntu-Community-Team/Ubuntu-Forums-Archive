---
title: "can't use fatsort if not a fat filesystem"
date: 2011-05-08
forum: Multimedia Software
---

### Post by spipe on 2011-05-08
I've been experimenting with an older Iriver music player - what it lacks in memory capacity, it makes up for in great sound quality, and I like that it understands OGG.

Problem is, copying files to it through Nautilus, the song order is arbitrary.  This is a deal breaker especially for audio books, which I sometimes want to listen to this way.  On my previous MP3 player I could use fatsort to fix file order, but the Iriver player doesn't use a vfat filesystem.  When it's connected via Nautilus, "mount" shows it as "binfmt_misc" type.

Does nautilus have the ability to sort files (internally, not just for display) on binfmt_misc mounts? Or is there some other way to do it?

---

### Post by spipe on 2011-05-25
I found a rather awkward workaround, which was to write some scripting around mtp-sendfile (from the mtp-tools package).  It at least lets me copy files in a specified order.

More elegantly, it would be nice if nautilus had an "enforced lexical order" copy option that worked independently of the destination filesystem type.  But I suppose not many people need that.

---

