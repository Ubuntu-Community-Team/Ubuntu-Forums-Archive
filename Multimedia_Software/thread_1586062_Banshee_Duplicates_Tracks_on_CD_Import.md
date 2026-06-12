---
title: "Banshee Duplicates Tracks on CD Import"
date: 2010-10-01
forum: Multimedia Software
---

### Post by djrobthaman on 2010-10-01
Hi,

Does anyone know how to fix this issue.  Whenever I import a CD each track is displayed twice in the library (but only one mp3 file is made) with one track displayed as being a few seconds longer than its duplicate.

I'm using Banshee 1.8.0

Thanks

---

### Post by icb410 on 2010-10-03
There's a bug report about this issue in the banshee bug tracker ([**Bug 614171**]("https://bugzilla.gnome.org/show_bug.cgi?id=614171")).  It seems turning off the Library Watcher extension before importing the CD solves it (it did for me).  Hopefully they fix the bug so this doesn't happen in the future.  If you get duplicates, rescan your library.

---

### Post by fgm@osinet.fr on 2011-10-18
Still there in Natty, though.

---

### Post by Hadogenes on 2011-11-18
I'm still seeing this behavior in 11.10.  I've turned off the Library Watcher extension, and I'll see if that helps.

---

### Post by PJSingh5000 on 2012-01-10
After import, I am able to remove the duplicates...

Right click on the album, select "remove from Library"
In the left panel, right click on "Music" and select "Import Media..."
In the dialog, select "Folders" from the drop-down
Click "Chose Folders..." button
Navigate to the location where the CD was imported
Click the "Import" button

The imported album will be reloaded without the duplicates.

---

