---
title: "VLC media player doesn't see files as &quot;media files&quot;"
date: 2010-01-22
forum: Multimedia Software
---

### Post by Objekt on 2010-01-22
I have an NTFS volume on my system which I regularly access from within Ubuntu 9.10, mostly to play the plethora of DVD images (*.iso files) stored there.  I use VLC Media Player to watch the content.

For some reason, VLC's file browser only shows a small subset of the files by default.  I have to select "All Files" instead of "Media Files" to see all the *.iso's.  

What's this about?  Since they're all the same type of file, I don't understand why some would be viewed as "media files" but others not.  If the files were on a Linux-type filesystem (ext3 etc.) I would guess it had something to do with permissions, but I'm not sure how file ownership & permissions apply to a mounted NTFS volume.

---

### Post by stinger30au on 2010-01-22
what version of vlc are you running???

click on help

about

---

### Post by Objekt on 2010-01-22
Wow, I wasn't expecting an answer THAT fast!  Thanks.  I'll look when I get a chance, later today.  I'm not at my Ubuntu 9.10 machine right now.

VLC version 1.0.2.

---

### Post by Objekt on 2010-04-14
I have VLC Media Player 1.0.5 ("Goldeneye").  I still have the problem with not all *.iso files being detected as "media files."  I have to set the file type to "All Files" in VLC's browser to truly see everything.

---

### Post by mc4man on 2010-04-14
I see no issue here as far as finding .iso's on an external drive (ntfs

What you could try is this 
```
sudo apt-get install qt4-qtconfig
```

Then in System -> Preferences -> Qt 4 Settings change the default gui to somethig other than 'default' or 'gtk+' - Cleanlooks works well with vlc.

Your file browser window will be a bit different, see it it works better.

(the default gui - gtk+, does not work perfectly with vlc in karmic and earlier, may be a bit better in lucid though I always change to Cleanlooks and never have any issues w/ vlc

---

### Post by Objekt on 2010-04-20
That worked!  Thanks.

---

