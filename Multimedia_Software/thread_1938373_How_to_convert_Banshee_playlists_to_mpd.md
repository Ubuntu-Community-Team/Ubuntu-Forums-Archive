---
title: "How to convert Banshee playlists to mpd?"
date: 2012-03-09
forum: Multimedia Software
---

### Post by Kurtosis on 2012-03-09
Does anyone know how to convert Banshee playlists into mpd-readable ones?  mpd doesn't seem to like .m3u playlists exported from Banshee, not much info on this on the web either.  Wondering if this is a solved problem but just not written about much?

---

### Post by papibe on 2012-03-10
Hi Kurtosis.

I've done it from Rhythmbox to mpd.

.m3u are just paths to files plus some comments. You can open them in gedit (or other text editor). My first guess is that the paths are relative to the ~/Music directory and mpd is set read the library in a different directory.

Just a thought.
Regards.

---

### Post by Kurtosis on 2012-03-12
Thanks papbibe, I've tried editing them and using both relative and absolute paths, but no luck.  Will keep at it.

---

### Post by Kurtosis on 2012-03-21
Finally got around getting this solved.  Problem is just the path issue.  The m3u file paths have to be the full, expanded path from / all the way to the music file:

/home/userid/music/library/path/to/song.mp3

Neither relative paths nor ~/... works:

../../.mpd/music/library/path/to/song.mp3
~/music/library/path/to/song.mp3

Wew, at last, no more resource-hogging kernel-panic-causing gui music players.

---

