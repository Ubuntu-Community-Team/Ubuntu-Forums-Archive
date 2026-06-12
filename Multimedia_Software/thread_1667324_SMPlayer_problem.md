---
title: "SMPlayer problem"
date: 2011-01-14
forum: Multimedia Software
---

### Post by rdragonov on 2011-01-14
I have my Home folder on its own partition and SMPlayer is set as my default media player. When I double-click on an mp3 the program opens but won't play the file. If I open an mp3 inside SMPlayer (Open>File) it plays. If I put an mp3 file on the *desktop* it *will* play on double-click.

Any ideas on how to fix this so I can open media files in SMPlayer by double-clicking?

---

### Post by andrew.46 on 2011-01-14
Hmmmm..... do the problem files have spaces in the filenames?

Andrew

---

### Post by rdragonov on 2011-01-15
Yes there are spaces. I just tried renaming an mp3 with no spaces and it will play on double-click.

Do you know of any way around this issue? I'd rather not have to rename my entire music collection.

---

### Post by cchhrriiss121212 on 2011-01-15
I had the same issue a while back. Set the default player to be this custom command:
smplayer %f

---

### Post by rdragonov on 2011-01-15
Thanks! That fixed it.

---

### Post by andrew.46 on 2011-01-15
Looks like I was too slow with the fix :). I discovered this issue a while back on my own system and posted on the SMPlayer forums:

xfce error with SMPlayer 0.6.9
[http://smplayer.berlios.de/forum/viewtopic.php?f=2&t=227](http://smplayer.berlios.de/forum/viewtopic.php?f=2&t=227)

So indeed the simple fix is to alter the .desktop file...

---

