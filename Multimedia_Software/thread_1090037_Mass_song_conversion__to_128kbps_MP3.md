---
title: "Mass song conversion  to 128kbps MP3"
date: 2009-03-07
forum: Multimedia Software
---

### Post by zekopeko on 2009-03-07
hi,

i want to convert (actually convert & copy) my entire collection of songs to 128kbps constant bitrate mp3's.

Now is there a sane way to do all of this:

-Copy my entire collection (from Music folder) to Music(128kbps) folder while maintaining folder hierarchy of the original Music folder. So basically i just want to have a 128kbps copy of my collection in another folder.

-The problem would be the variety of file formats that i have. everything from mp3,ogg,wma,mp4,flac etc.

-If the files are of lower quality (less then 128kbps) then they shouldn't be converted.

-Use multiple cores for speed (wishlist item). 

-Strip any embedded cover art (wishlist item).

So any automated way to do this?

---

### Post by tgalati4 on 2009-03-07
A fancy script using sox would do it.

You could load amarok or banshee with your library then use an mp3 player with 128 kbps re-encoding set and load your player.

You could set up an icecast server then stream to another machine with 128 kbps reencode set.  Use  streamripper to capture the song files with directory structure.  This is a slow method since it only works realtime.

---

