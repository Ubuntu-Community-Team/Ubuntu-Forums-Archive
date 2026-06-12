---
title: "Creating playlists for a Creative Zen Style music player (possibly .pla?)"
date: 2011-12-26
forum: Multimedia Software
---

### Post by oddparticle on 2011-12-26
I'm trying to create a playlist on my mp3 player (a Creative Zen Style M100), have spent hours googling, and had no luck so far. I can't find for certain which formats it needs, although it may be .pla. I can't find any way to create .pla files. And none of the playlist files I can create will work on it (m3u, pls or xspf).

I have tried the instructions posted elsewhere on here for creating a .pla file by saving as m3u in Banshee then editing the file extension, and this file wasn't recognised... The best result I've had has been with .m3u, which at least appear on the device, but it claims they don't contain any tracks.

The documentation has been no help at all - it says nothing about supported formats and tells me to use Windows Media Player.

So, I am completely stuck. Any help at all would be hugely appreciated, or even any definite information about supported playlist formats for the thing... I'm not enormously technical, so if there is a music player that can export playlists in the right format, or a conversion script I can run, that would be ideal. Thanks!

---

### Post by andrew.46 on 2011-12-27
I am not familar with the device unfortunately but certainly there is more than one way to have a playlist:

[http://en.wikipedia.org/wiki/Playlist#Types_of_playlist_files](http://en.wikipedia.org/wiki/Playlist#Types_of_playlist_files)

Perhaps try a simple *.pls *file which simply has the path and filename of each of the songs in the playlist, one per line. This can be made with a simple text editor. Otherwise I am afraid I can be of little help :(.

---

### Post by ruzvfaiv on 2011-12-28
I had the same problem, and somehow managed to solve it.

.pla playlists can be created with Rhythmbox, but they don't seem to work in Zen Style M100. And playlists that worked for me are .m3u8 and .m3u (but also with UTF-8 ).

I have created .m3u and .m3u8 playlist also with Rhythmbox and edited with Gedit to change encoding and correct file paths. To create a working playlist I copied tracks to Music directory in ZEN, added these tracks to Rhythmbox, created a playlist and saved it into Playlist direcory in ZEN. Then opened that playlist with Gedit and modified track directories. The thing to change in track directories is to make track directory root the device root. For example my device mounts at "/media/MY ZEN", so the tracks are found (and also created in playlist) in "/media/MY ZEN/Music/myDirectory/MyTrack.mp3". So this directory needs to be changed to "/Music/myDirectory/MyTrack.mp3" the first slash meaning the ZEN root.

After changing all directories like that the playlist opened and finally had some tracks. :)

---

