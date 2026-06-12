---
title: "Audio Library and Metadata Woes :-)"
date: 2010-08-14
forum: Multimedia Software
---

### Post by Erulisseuiin on 2010-08-14
This is an interesting problem. I'm trying to find a way to reconcile metadata (playcounts, ratings, id3tag updates, etc.) in an audio library with multiple formats for each song. example

/home/username/Music/flac/Album/Somesong.flac
/home/username/Music/mp3/Album/Somesong.mp3
/home/username/Music/vorbis/Album/Somesong.ogg


Ideally what I would like is a bash script that runs through the flac files and updates the mp3 and vorbis files accordingly. 

Another part of this problem is the current lack of duplicate detection in media players If your library has 3 copies of a song (in 3 different formats) the media player should try to revert to the highest quality available, and only display one song, (as opposed to 3) however these features seem to be missing in all media players  :-)

Has anyone else ever dealt with these problems?

**As a note**: I found a forum thread with a solution *close* to what i am looking for 
[http://ubuntuforums.org/showthread.php?t=1096665](http://ubuntuforums.org/showthread.php?t=1096665)

The problem with this solution however is that it converts a flac file to an mp3, I already have the mp3's I just want to touch up the metadata.

---

