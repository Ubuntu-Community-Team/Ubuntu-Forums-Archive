---
title: "Copied DVDs Won't Play"
date: 2013-01-18
forum: Multimedia Software
---

### Post by BubbaBlues on 2013-01-18
There is a problem with the latest version of libdvdnav4. Any dvd you copy with k9copy
or dvd95 with a menu will not play on the computer or a home dvd player.  They just choke when trying to read the menu.  

"libdvdnav is a DVD navigation library, which provides an interface to the
advanced features of DVDs, like menus and navigation. It contains the VM and
other parts useful for writing DVD players. It's based on Ogle, but was
modified to be used by xine and mplayer."

They used to play perfectly before  4.2.0+201...  and it doesn't matter what distro 
or desktop environment you try.  
 Is there a way to change that file with an earlier version?

I could be totally wrong , but it's my best guess.  Whatever the problem is, you can not copy a dvd onto a single layer disk
with k9copy that will play anymore.  Not if you keep the menu.

---

### Post by dpurgert on 2013-01-18
best guess would be to send a bug report to the package maintainer.

not familiar enought with libdvdnav to know how you'd go about kicking it back to an earlier version though :|

---

### Post by BubbaBlues on 2013-01-18
Yeah, I don't really know enough either.  I don't want to send a bug report on it
if that isn't the problem. If I could try an earlier version of that and keep everything 
else current, then I'd know. ;)

---

### Post by Johnny Buffalkill on 2013-01-23
I have the same problem, so instead of starting a new thread, I'll reply/bump here.  Whenever I try to shrink a DVD with K9 copy, the result is unplayable.   I only rip these to my HDD, I've never tried burning a disk.  Whether its a folder, or iso, it just crashes whichever media player I try.

I'm running ubuntu 12.10.  It worked fine in my 11.10 installation, which I still have, so I can get the job done, but thats kind of a clumsy workaround.

It never occurred to me it could be libdvdnav causing the problem.  I can still navigate other DVDs just fine, its only when I shrink them that the result doesn't work.  DVDs that I shrink with my older installation work as well.      It might be useful to hear if anyone else has tinkered with this and found any information.

---

