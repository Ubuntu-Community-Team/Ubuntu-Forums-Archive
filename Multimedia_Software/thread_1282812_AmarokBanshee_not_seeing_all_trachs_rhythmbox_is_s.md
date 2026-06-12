---
title: "Amarok/Banshee not seeing all trachs rhythmbox is seeing"
date: 2009-10-04
forum: Multimedia Software
---

### Post by peterson_espacoporto on 2009-10-04
Hello,

I'm using Karmic Koala now, but this is something I've noticed even in Jaunty. In my Music folder:

Nautilus sees 2785 files;
Rhythmbox sees 2785 files;
Amarok sees 2782 files
Exaile sees 2782 files
Banshee 1.5 (beta) sees 2782 too

Any reason for this? Is there a way I can compare databases so I could check what files are being considered by ones and not by others?

---

### Post by vinutux on 2009-10-05
I think prob related to file size ...those apps not deals with small sized files (below 1 mb or so)

---

### Post by peterson_espacoporto on 2009-10-05
Humm I don't think so. The only file I could think of as being so small was a CD intro which had 852 kb, but Amarok recognized it..

---

### Post by peterson_espacoporto on 2009-10-05
OH I finally found out what the problem was. EXTENSIONS.

It seems that all the apps except for rhythmbox only consider *.mp3 files. Somehow this sounds weird to me, I'm so used to not needing extensions in linux =S

But anyhow, I already found two songs like that (by accident, as I was trying to find them in Amarok). Is there a way to easily find the last one?

---

