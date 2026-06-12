---
title: "[SOLVED] Amarok has every song twice!"
date: 2007-08-20
forum: Multimedia &amp; Video
---

### Post by Zalbor on 2007-08-20
Basically that's it. Going to "collection" and expanding a band and an album, any one, every song in it appears twice. If I drag the album to the playlist, each song is added twice in a row.
Yes, I only have one file for each song. What could be causing this, and can it be fixed?

---

### Post by benhagerty on 2007-08-20
Do both songs work normally?

---

### Post by cookies on 2007-08-20
Try 

Playlist > Remove Duplicate & Dead Entries

---

### Post by Zalbor on 2007-08-20
The playlist thing only works in the playlist, the problem was in the collection.

I did something that fixed it, I don't understand how though. It seems that it was set to look for songs only under /media, while I wanted it only under /music (which is a symlink to a folder that's somewhere under /media).
I changed it back and each song exists once now, but I don't get how it happened. Since only /media was checked, it should still have found each file only once.

---

