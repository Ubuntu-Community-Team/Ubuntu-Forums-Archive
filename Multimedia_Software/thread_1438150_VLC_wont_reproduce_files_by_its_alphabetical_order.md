---
title: "VLC wont reproduce files by its alphabetical order"
date: 2010-03-24
forum: Multimedia Software
---

### Post by hihihi100 on 2010-03-24
Hello there:

This problem has been here for 2 months or so:

If I, in VLC, choose a folder with several mp4 or other multimedia format files, it will show em in the playlist in random order, definitively not alphabetical. that didnt use to happen before.

Tips?

---

### Post by Chronon on 2010-03-24
There's apparently a bug that causes segfaults when sorting the playlist in VLC 1.0.2.  This might be related to that.  It's apparently fixed in more recent versions of VLC.

---

### Post by hihihi100 on 2010-03-25
more recent versions of VLC...

Is there any more recent version than 1.02? Ubuntu software center and synaptic both show 1.02 as the standard

---

### Post by Chronon on 2010-03-25
You would have to install manually.  The version in the Karmic repositories is 1.0.2.  The source tarball on their site is currently 1.0.5.  I will probably just wait until a new version is packaged.

---

### Post by Devport on 2010-03-25
You can get a newer version at

[http://www.getdeb.net/updates/Ubuntu/9.10/?q=vlc](http://www.getdeb.net/updates/Ubuntu/9.10/?q=vlc)

Dont know if in 1.0.5 this bug has been fixed.

---

### Post by Chronon on 2010-03-25
At least the segfault when sorting playlists is supposed to be fixed, according to a discussion I saw on VLC forums.

---

