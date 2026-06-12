---
title: "VLC isn't FLAC friendly"
date: 2008-09-20
forum: Multimedia Software
---

### Post by linuxvacuum on 2008-09-20
When I play some of my FLAC encoded files VLC doesn't play them until the end and skips to the next one in my playlist. This is VERY annoying. I thought VLC 0.9.2 fixed that. It is fixed in a way, instead of skipping the song will pause and then continue. I really don't want to use a another media player through wine to play my music.

---

### Post by ladr0n on 2008-09-20
I don't know about VLC, as I don't use it for anything other than DVDs.  However, before wine'ing winamp or something, I would look into amarok, banshee, mpd, exaile, rhythmbox, etc.  There are so many media players for linux, you're sure to find one that does what you like (and they should all play flac).

---

### Post by linuxvacuum on 2008-09-21
Maybe I could reencode all my files to a FLAC version that works best with VLC. Anyone else has that problem?

---

### Post by linuxvacuum on 2008-09-21
Here is a sweet command to simply reencode your FLAC files to FLAC files. Yes that is right, if like me you want to reencode your old FLAC files to the latest version. Enter the following in a terminal :

> find /directorycontainingflacfiles/ -type f -regex '.*\.flac' -exec flac -force {} \;

The find commands lists all files that ends with the .flac extension (thanks to the regular expression) then the listed filenames are entered in the flac program. It will also go into the sub directories.

---

### Post by bark50 on 2008-09-27
> **linuxvacuum said:**
> Maybe I could reencode all my files to a FLAC version that works best with VLC. Anyone else has that problem?

For me, VLC plays FLAC files with sputters and pauses and skips.  It won't play my WMA files at all.  If not for these problems, I would really like VLC.

---

### Post by tariquepark on 2008-09-27
hi all
has anyone tried xine?
i use it for everything now no probs at all

---

