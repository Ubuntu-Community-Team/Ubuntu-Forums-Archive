---
title: "Amarok with OGG Player"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by Deived on 2007-10-19
I got a new portable media player, the Meizu M6 Miniplayer.  It works great in Linux because it doesn't need any special software for transfer, converting video, and restoring.  Anyway, I'm having one problem with it when using it with Amarok.

Amarok sees the player and assigns it as Generic Media Player (or whatever it says, im away from that computer right now).  I'm able to see the contents in Amarok and it's also able to transfer MP3s to it, however most of my music is in OGG.  When I attempt to send an OGG to it, it gives an error saying that the player doesnt support OGG (or something like that).  When I try to configure the player in Amarok and add other media types that it supports (MP3, OGG, FLAC, APE), that setting doesnt stay.  I'll add the types and click OK, but when I open up the config again, it only has MP3 and not everything else I just added.  As a note, it does keep the folder location of where to send the media.  By default it sends it to the root of the player (/media/meizu) but I changed it to /media/meizu/MUSIC and that setting stays, but just not the media types.

Any help?
Sorry if I'm not making much sense.  Im trying to be fast because I'm at work.

---

### Post by Deived on 2007-10-20
::BUMP::

Anyone?

---

### Post by mfraser on 2007-10-28
> **Deived said:**
> I got a new portable media player, the Meizu M6 Miniplayer.  It works great in Linux because it doesn't need any special software for transfer, converting video, and restoring.  Anyway, I'm having one problem with it when using it with Amarok.

Amarok sees the player and assigns it as Generic Media Player (or whatever it says, im away from that computer right now).  I'm able to see the contents in Amarok and it's also able to transfer MP3s to it, however most of my music is in OGG.  When I attempt to send an OGG to it, it gives an error saying that the player doesnt support OGG (or something like that).  When I try to configure the player in Amarok and add other media types that it supports (MP3, OGG, FLAC, APE), that setting doesnt stay.  I'll add the types and click OK, but when I open up the config again, it only has MP3 and not everything else I just added.  As a note, it does keep the folder location of where to send the media.  By default it sends it to the root of the player (/media/meizu) but I changed it to /media/meizu/MUSIC and that setting stays, but just not the media types.

Any help?
Sorry if I'm not making much sense.  Im trying to be fast because I'm at work.

Not that it's going to help you much, but this is happening to me now.

---

### Post by gottferdamnt on 2007-12-03
Same Issue HERE ! Please help !

---

### Post by fondle-em on 2007-12-03
This is a ugly little Amarok bug that slipped through, but there is a workaround.  Amarok is basically corrupting its own Generic Media Player preferences with garbage "&" characters.  Amarok is then ignoring the corrupted preferences, which is why it looks like the changes aren't sticking - Amarok disregards the corrupted lines.  I use Generic with a Rockbox-enhanced iPod and [this is what worked for me]("http://bugs.kde.org/show_bug.cgi?id=151806#c8").

---

### Post by gottferdamnt on 2007-12-06
thank :]

---

### Post by ZolaMoukoko on 2007-12-24
> **fondle-em said:**
> This is a ugly little Amarok bug that slipped through, but there is a workaround.  Amarok is basically corrupting its own Generic Media Player preferences with garbage "&" characters.  Amarok is then ignoring the corrupted preferences, which is why it looks like the changes aren't sticking - Amarok disregards the corrupted lines.  I use Generic with a Rockbox-enhanced iPod and [this is what worked for me]("http://bugs.kde.org/show_bug.cgi?id=151806#c8").

Thanks for this work around - it works perfectly.

---

