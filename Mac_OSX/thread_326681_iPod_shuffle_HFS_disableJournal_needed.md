---
title: "iPod shuffle: HFS disableJournal needed?"
date: 2006-12-28
forum: Mac OSX
---

### Post by ChrisC on 2006-12-28
I just got an iPod shuffle and initial searching in these forums led me to believe that I need to disable journaling in the device's filesystem before manipulating mp3 files on the device.  But now I'm wondering if those instructions only applied to larger disk-based iPods.  Does the iPod shuffle (2nd gen, in my case) Just Work when plugged into an Ubuntu system (i.e. show up as a mounted USB drive and allow read/write access) or do I indeed need to do the diskutil disableJournal command first on a Mac OSX machine?

---

### Post by ChrisC on 2006-12-28
And is it correct that I can just copy the mp3 file in and it'll get recognized as playable?  Or MUST I use an app (gtkpod?) that rebuilds the device's database?

---

### Post by 3rdalbum on 2006-12-28
Ipods, even the Shuffle, require the database. If you copy an MP3 file onto it, the iPod won't recognise it unless it has an entry in the database. So, yes you need Gtkpod.

iPods come either unformatted or with a Fat32 filesystem. It will only be HFS-formatted if you've done a "restore" with a Mac OS X system. If it has been HFS-formatted, then you still need to disable journalling - the journalling, not the size, is what stops reliable writing in Linux.

---

