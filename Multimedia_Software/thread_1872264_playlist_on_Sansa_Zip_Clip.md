---
title: "playlist on Sansa Zip Clip"
date: 2011-10-30
forum: Multimedia Software
---

### Post by Wobblybob on 2011-10-30
Hi, 
I have just received my Clip Zip and have been playing with it for a few days now. I use Ubuntu & Debian and therefore copy music, podcasts etc to it using the MSC mode drag and drop but so far have not managed to get a playlist to show up in the playlist menu let alone play the listed songs. The .m3u format is supported and I have tried using a text editor to create one, copying across playlists from rhythmbox after running them through sed to replace / with \ and the fromdos package to convert all LFs to CRLFs and I also used easytag as per [http://forums.sandisk.com/t5/Clip-Clip/HOWTO-Creating-m3u-Playlists-using-easyTAG-on-Linux/td-p/3350]("http://forums.sandisk.com/t5/Clip-Clip/HOWTO-Creating-m3u-Playlists-using-easyTAG-on-Linux/td-p/3350") this thread all with no luck so far. the music is stored on the clip zip in a MUSIC directory in the format <Artist><album><song.mp3> so the playlist look like this;

```
#EXTM3U
#EXTINF:225,Artist - Song name1
Artist\Greatest Hits\Song name1.mp3
#EXTINF:335,Artist - Song name2
Artist\Greatest Hits\Song name2.mp3
```
and I've tried putting it in the MUSIC Directory as is or in the root of the Zip Clip after adding the MUSIC folder to each line and even removing all the path info and placing it in the album sub folder with no luck. has anyone managed to get this working?

---

