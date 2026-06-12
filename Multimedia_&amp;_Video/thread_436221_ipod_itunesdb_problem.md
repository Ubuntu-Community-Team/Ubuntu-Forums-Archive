---
title: "ipod itunesdb problem"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by chris rowan on 2007-05-07
gtkpod and amarok both read the itunes database of my ipod nano without difficulty, and new tracks and playlists can be added. 

Having synced, saved changes and disconnected, I note that while new playlists and tracks show up on the ipod, the new tracks (mp3s) wont play. 

If I add the same track to my itunes library under 'doze, there is no problem. 

I can only assume that for some reason, gtkpod and amarok are not writing to the ipod database correctly.

Any suggestions? 

(Incidentally when I connect to my ipod in gtkpod I am informed that there is a checksum discrepancy between the database file and its extension)

---

### Post by chris rowan on 2007-05-08
just re-initialised ipod and startd again. 

All tracks successful except mp3s ripped with cd-dax tractor in crossover. (mp3s previously ripped in 'doze work fine) 

Also, the mp3's ripped with daxtractor will go on the ipod successfully within itunes.

I am using Feisty, btw

Cheers

---

### Post by chris rowan on 2007-05-08
- and the only difference between my ubuntu-ripped mp3s and media-player ones is the bitrate (32 kbps on ubuntu, 128-320 on media player). Again, itunes can handle these low bitrate mp3s.

---

### Post by chris rowan on 2007-05-12
turns out the problem was in using cda-xtractor alongside gtkpod. I tried a different ripper (freerip) and all works ok.

---

