---
title: "copy (and paste) / drag and drop symlink targets"
date: 2010-10-26
forum: Mythbuntu
---

### Post by MrBeReady on 2010-10-26
I have set up mythlink.pl to make human-readable symlinks to my recordings in /var/lib/mythtv/pretty. That's all working fine.

I want to be able to plug in a USB thumb drive and copy a recording to it using the "pretty" filename. When I use Thunar to browse to the /var/lib/mythtv/pretty directory and try to copy using the symlink, it copies the symlink to my USB drive instead of the underlying target file.

If I use cp in a terminal to copy a link in /var/lib/mythtv/pretty to my USB drive, I do get the target file, not the symlink. Is there a way to do this in Thunar? Or another GUI file manager?

---

### Post by nickrout on 2010-10-27
are you saying cp is not a file manager?

Maybe mc will do it.

---

