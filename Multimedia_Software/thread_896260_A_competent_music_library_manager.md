---
title: "A competent music library manager?"
date: 2008-08-21
forum: Multimedia Software
---

### Post by yang on 2008-08-21
Is there a music library manager out there that can reorganize my files/directories like iTunes does?  Amarok has 'Organize Files', but in an embarrassing design bug, their playlists are path-based instead, meaning that your existing playlists are rendered useless upon reorganization.  Amarok 2, whose beta is released in the next ~24 hours, will supposedly use proper references (in a relational database), but given Amarok's stability track record and in light of these bugs, I might hold off on being a beta-tester.

In the meantime, I've tried Amarok and Exaile; the latter does not seem to support organizing files.  I've also read up a bit on Songbird, Jajuk, Listen, Banshee, and Quod Libet, but they don't sound very promising.  Last time I tried Songbird, it was quite unusable.  Jajuk is the only other one that mentions 'organization,' but it also mentions it uses the same m3u-based playlists as Amarok.

So...I've been investing some time doing research, but I'm about to give up.  Any other leads or more details/corrections about these applications?  Thanks in advance!

---

### Post by yang on 2008-08-22
I just tried some more:

Songbird has no file/dir reorganization feature.

Amarok 2 beta's file/dir reorganization feature is disabled (causes it to crash).

---

### Post by tangibleorange on 2008-08-22
what's wrong with rhythmbox (applications -> Sound & Video -> Rhythmbox)?

once you tell it where all your music is, it will add everything in that file (and sub directories like iTunes), and even update if you add new files to the folder. now AFAIK, even iTunes can't do that!

---

### Post by yang on 2008-08-22
Even though it has "Library Structure" settings, rhythmbox doesn't actually reorganize my music into appropriate files/dirs.  I believe that setting is only used for ripping music.

---

### Post by tangibleorange on 2008-08-22
> **yang said:**
> Even though it has "Library Structure" settings, rhythmbox doesn't actually reorganize my music into appropriate files/dirs.  I believe that setting is only used for ripping music.

ah sorry i misunderstood. in that case, i'm stumped. all i know of are tagging applications which rename the files, not organise them into dirs. i use a tagging application and then simply create the folders myself. Mind you, my music collection has about 700 songs. If you've got 5000+, i can imagine it would become pretty tedious :lolflag:!

---

### Post by hugmenot on 2008-08-23
Quod Libet can reorder your library. It's not a single click command, but you can select a bunch of files (even all your library at once) and then open the tag dialog. Go to the Rename tab and enter a pattern you want, like

```
/home/blah/music/<artist>/<album>/<tracknumber>. <title>
```

When you press Save all selected files will be moved around your filesystem, so they are in the folder hierarchy you specified. Words in <angle brackets> are tag names. A slash creates a new directory of course. Your playlists will be preserved I think.

*tagging as recurring discussions*

---

### Post by hugmenot on 2008-08-23
[http://www.sacredchao.net/quodlibet/wiki/Guide/Renaming](http://www.sacredchao.net/quodlibet/wiki/Guide/Renaming)

---

### Post by yang on 2008-08-23
But my question was: will its playlists potentially break after the rename?

---

### Post by hugmenot on 2008-08-23
I just checked for you. They still work. The playlist was rewritten after I renamed the files. It's all transparent.

---

