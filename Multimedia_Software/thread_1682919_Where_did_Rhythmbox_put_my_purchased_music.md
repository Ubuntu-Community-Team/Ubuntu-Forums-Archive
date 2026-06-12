---
title: "Where did Rhythmbox put my purchased music?"
date: 2011-02-06
forum: Multimedia Software
---

### Post by temporos on 2011-02-06
I recently downloaded some music from the UbuntuOne store.  They downloaded fine (although it took a while), but I cannot locate them in my music folder.  I have the default folder in Rhythmbox set as *~/Music*, but my downloaded music isn't in there.  They play fine in Rhythmbox and my iPod, but I can't find them in the file system.

Why isn't Rhythmbox putting my purchased music in the default music folder?

---

### Post by Tristan Tonks on 2011-02-07
Have you tried the 'downloads' folder?

next stop ...

Have you tried the 'tmp' folder in root?

open a folder view and select the up arrow on the window 'frame'. by default folders open in your 'My Documents' Folder, the next highest level is the 'Home' folder then after that is the 'root' directory which has a folder in it called 'tmp' this is a safe-house for items downloaded by programs.

---

### Post by temporos on 2011-02-07
I found the files in the following location:
```
~/.local/share/ubuntuone/Purchased from Ubuntu One/
```
This is strange, because my default download directory in Rhythmbox is set as *~/Music*.

Any idea why this might be happening?  I would just move them to the *~/Music* directory, but that would screw up the sync with UbuntuOne, as well as forcing me to reload them into Rhythmbox. :-k

---

### Post by mjones41 on 2011-03-08
I'm still waiting for my album to download 24 hours later.  This is the 4th time I have bought music from Ubuntu one, I get the music in the end but it is always a pain.  I don't get why it has to be so difficult.

---

