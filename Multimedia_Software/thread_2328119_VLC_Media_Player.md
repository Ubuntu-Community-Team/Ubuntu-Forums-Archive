---
title: "VLC Media Player"
date: 2016-06-17
forum: Multimedia Software
---

### Post by dannyk2 on 2016-06-17
Wonder if anyone could tell me how i might get VLC Media Player to play all the music tracks in sequence?
Thanks

---

### Post by RogueFactor on 2016-06-17
Usually you would just create a playlist

**View-->Playlist** or **CTRL+L**

Then just add in the music tracks in what order you would want them to play.
(Either by dragging and dropping or by selecting your media library on the left-handed panel)

---

### Post by ajgreeny on 2016-06-17
Either add all your music tracks to a new playlist and simply play that or go to the Media menu -> "Open multiple files" and add them there.

You can also choose "Open directory" from the same menu.  If all your music is in the Music folder in your home choose to play that and everything will be added, subfolders included.

---

### Post by TheFu on 2016-06-18
> **dannyk2 said:**
> Wonder if anyone could tell me how i might get VLC Media Player to play all the music tracks in sequence?
Thanks

I create an M3U playlist.

```
\ls -1 *mp3 > files.m3u
```

Then edit the order with any text editor and open the playlist in almost any player.
I use something like this to scan a music collection looking for albums of "greatest" or "best."  Since the files are in different directories, **find** is my tool of choice.  Using **ls** can be dangerous since the output can change.

---

### Post by gordintoronto on 2016-06-18
For this task, audacious is much easier to use.

---

