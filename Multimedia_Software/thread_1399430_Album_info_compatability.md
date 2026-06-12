---
title: "Album info compatability"
date: 2010-02-05
forum: Multimedia Software
---

### Post by newb85 on 2010-02-05
I've noticed some quirky behavior surrounding the tags on songs.

All the music I had ripped in Windows (in wma or mp3) behaves normally.

The music I ripped with Sound Juicer, or ripped with VLC and tagged with EasyTag both have the same tag issues.  The tags work great system-wide in Ubuntu, and if I drop the song on a data CD and put it in my Pioneer stereo, the tags work there, too.  I can put the song on my Walkman and then copy it to another Ubuntu machine, and the tags work on the second machine, as well.

However, the Walkman lists the song as Unknown Song, Unknown Artist, Unknown Album.  Further, if I transport the file into Windows, the Windows system doesn't recognize the tags, either.

This begs the question, are there multiple tag formats?

---

### Post by newb85 on 2010-02-17
A little more research revealed:

The tags on mp3 files are called ID3 tags, and there are, in fact, different versions.  Sound Juicer and EasyTag both use version 2.4 by default.  Walkman and Windows are equipped to read only version 2.3 and older.  I changed the preferences in EasyTag to use version 2.3 and retagged the mp3 files, and presto!  The file tags were suddenly recognized everywhere.

---

