---
title: "Sansa Fuze+ Playlist issues"
date: 2013-05-30
forum: Multimedia Software
---

### Post by dubie18 on 2013-05-30
I've spent all day Googling and trying to get playlists to work on my Sansa Fuze+.  I've followed various tutorials, and currently I have my sansa in MSC mode, with all my music in the Music folder(incidentally, Banshee stuck it all in the root, despite the .is_audio_player).  I have a playlist called test.m3u in the Playlists folder, with contents as follows:

```

#EXTM3U
#EXTINF:107,00 - All My Loving.mp3
../MUSIC/Across The Universe Cast/Unknown Album/00 - All My Loving.mp3
#EXTINF:259,00 - Come Together.mp3
../MUSIC/Across The Universe Cast/Unknown Album/00 - Come Together.mp3
#EXTINF:138,00 - Dear Prudence.mp3
../MUSIC/Across The Universe Cast/Unknown Album/00 - Dear Prudence.mp3
#EXTINF:241,00 - Hey Jude.mp3
../MUSIC/Across The Universe Cast/Unknown Album/00 - Hey Jude.mp3
#EXTINF:130,00 - I've Just Seen a Face.mp3
../MUSIC/Across The Universe Cast/Unknown Album/00 - I've Just Seen a Face.mp3
#EXTINF:192,00 - While My Guitar Gently Weeps.mp3
../MUSIC/Across The Universe Cast/Unknown Album/00 - While My Guitar Gently Weeps.mp3


```

However, what displays is an empty playlist.  I have also tried backslashes, Music instead of MUSIC, and sticking it in the root directory.  I've tried generating a playlist from Banshee, Rhythmbox, and EasyTag.  The firmware is version 02.38.06 A, which is the most recernt version as far as I can tell.  Has anyone had any success with this, or a sample .m3u file that works?

---

### Post by RavenLX on 2013-09-05
I know this is way late but I hope this article will help you:
{removed link at poster's request.}

I just got a Sansa Clip+ and wrote up some information on how to create playlists.

The key thing here is that you need to remove all ../MUSIC from each line and then change all / to \ so that it can find the file. My tutorial in the link above covers how to do that and also what to do if the player won't turn off. And I have a tutorial on how to upgrade the firmware in the article as well. 

Hope this helps the OP and/or anyone else that runs into these problems.

---

