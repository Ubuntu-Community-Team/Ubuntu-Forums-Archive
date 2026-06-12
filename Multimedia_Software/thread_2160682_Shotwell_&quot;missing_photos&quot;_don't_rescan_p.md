---
title: "Shotwell &quot;missing photos&quot; don't rescan properly"
date: 2013-07-07
forum: Multimedia Software
---

### Post by pjjjv on 2013-07-07
Similar to this thread [http://lists.yorba.org/pipermail/shotwell/2013-April/004812.html](http://lists.yorba.org/pipermail/shotwell/2013-April/004812.html), I accidentally disconnected my external storage and started Shotwell. Now 8000 photos (32%) are under "Missing photos". However when I've reattached the external storage and restarted Shotwell, they do not migrate back to the main library. This feature should be working as mentioned on [http://www.yorba.org/shotwell/help/other-missing.html](http://www.yorba.org/shotwell/help/other-missing.html). I'm mostly interested in one specific label tag. Behavior is exactly the same as in that thread. Some new info I can offer is that I use a softlink (ln -s) to access that external storage and that this link path is in all of the photo filenames. Also, I'm using cinnamon and no nautilus (possibly dbus is missing for file modification updates??).

I even tried to use  "UPDATE PhotoTable SET flags=0, file_format=1 WHERE flags=8;" on a (copied) database to try and fix it but I don't understand the full sql logic yet. The photos go back to the main database then, but I lose the tags. I think the "backlinks" column is the culprit.

Anybody?

---

### Post by seanlano2 on 2013-11-22
Did you ever sort this out? I'm having a very similar problem, where I had an external hard drive with some of my photos, and I then imported new photos to a local location on my laptop. I then removed the hard drive, but still was able to use Shotwell with the remaining photos, as well as importing new ones. I've since edited these new ones, and I now wish to re-combine all my photos together.   > I have a working backup of the Shotwell database from before I removed the hard drive (which works just fine with the old photos, but obviously doesn't have the new photos in it). > I have a backup of the new Shotwell database (which works fine with the new photos, but has the problem of not properly re-associating the edited files > I have a backup of all my photos.  So, I have been able to experiment. I tried using sqliteman to edit the "flags" field in the "phototable" to 0 (I noticed the missing files were tagged with "8"), but this had the same problem of losing the associated events, tags, and also lost the edits too.  I'm going to keep trying, but any suggestions are most welcome.

---

