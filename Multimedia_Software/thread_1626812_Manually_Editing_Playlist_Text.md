---
title: "Manually Editing Playlist Text"
date: 2010-11-20
forum: Multimedia Software
---

### Post by amorphouskev on 2010-11-20
Can Anyone tell me what the format for the text of a playlist file? I'm using Songbird, and trying to get it to recognize either M3U or PLS files, and it's not. My .m3u/.pls file shows the following text:

[playlist] 
X-GNOME-Title=Playlist
NumberOfEntries=97 
File1=file:///home/kevin/Music/My Music/artist/album/singer-song.mp3 
File2=file:///home/kevin/Music/My Music/artist/album/singer-song.mp3

I save it as .m3u or as .pls and no audio player will recognize it (amarok, banshee, rhythmbox, songbird etc...)

---

### Post by Chronon on 2010-11-20
An m3u playlist is just a series of paths (each line contains a path to a track).  This is apparently some other format (maybe pls?).  There is EXTM3U info that can be used in M3U playlists, but this isn't consistent with that.

I can't answer about whether Songbird should play this type of playlist, though.  Sorry.

---

### Post by luigi_mb on 2010-11-20
Get "extm3u.pl" from

[http://www.splitbrain.org/projects/extm3u](http://www.splitbrain.org/projects/extm3u)

It does a good job!

/luigi

---

### Post by Chronon on 2010-11-20
Those aren't #extinf tags, though.  This isn't an m3u playlist, so you can't add extm3u data (#extinf tags and an #extm3u header) to it and expect players to understand the resulting file.  (Maybe the perl script you linked does something else but I can't really know that with the given information.)

It looks to be a PLS playlist: 
[http://en.wikipedia.org/wiki/PLS_(file_format](http://en.wikipedia.org/wiki/PLS_(file_format))

---

