---
title: "Advanced music player for linux"
date: 2017-05-07
forum: Multimedia Software
---

### Post by rony.n on 2017-05-07
Hello, 

Any music player out there that can shuffle one song at a time from multiple playlists ?
meaning I create 3 playlists and shuffle between them without playing two songs in a row from same playlist.

thank you

---

### Post by wildmanne39 on 2017-05-07
*Thread moved to **Multimedia Software**.*

---

### Post by Dennis N on 2017-05-07
> **rony.n said:**
> Hello, 
Any music player out there that can shuffle one song at a time from multiple playlists ?
meaning I create 3 playlists and shuffle between them without playing two songs in a row from same playlist.
thank you
If you intend to play through all available songs, then the requirement of no back-to-back play from the same list can't be satisfied in most cases. With many unequal size lists, eventually only one list will have songs to play.

For example,

Lists A, B, C
n(A)=50, n(B)=20, n(C)=10
Cycle A > B > C
after 10 cycles, list C is unavailable.
In 20 more cycles, list B is unavailable.
All remaining songs are in list A.

If you remove the restriction of no instance of back-to-back songs from the same playlist, then Audacious can do this.

---

### Post by rony.n on 2017-05-07
I already tried audacious, created playlists but I can't find out how to shuffle between all of em

---

### Post by Dennis N on 2017-05-07
> **rony.n said:**
> I already tried audacious, created playlists but I can't find out how to shuffle between all of em

Your playlists have to be exported as **.pls** files before you start - they can't just exist on a tab in Audacious. For each tab, use **Menu > Playlist > Export**. I have a separate folder in Music for keeping these playlist files.

1) Create New Empty Playlist (Menu > Playlist > New)
2) Use Add Files (Menu > Files > Add Files), but instead of adding individual music files, browse to your playlist files folder, and, selecting and then adding one playlist at a time*, add each of the existing playlists you want to use.
3) Set to Shuffle Mode and start playing.

*let each load into the player before adding another.

---

