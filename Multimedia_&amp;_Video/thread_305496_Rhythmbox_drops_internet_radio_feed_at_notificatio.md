---
title: "Rhythmbox drops internet radio feed at notification update"
date: 2006-11-23
forum: Multimedia &amp; Video
---

### Post by Extr3me on 2006-11-23
I have been having problems with Rythmbox on Edgy Eft where it drops the internet radio feed everytime it posts a notification.

Typically, the notification displays the track that is playing.  Each time the radiostation updates this info, it seems to drop the connection forcing me to reload the radio feed after every song.

This is something that seems to be new to Rythmbox in Edgy Eft, I had not seen this in Dapper Drake (6.06).

It is a fully updated install of 6.10, whilst using an .ogg radio feed.

Any suggestions or feedback would be cool.

---

### Post by Spyke on 2006-11-27
Apparantly, it isn't only Rhythmbox that is experiencing difficulties with the stations. Totem is affected too, so I'd suggest it's a gstreamer problem.

---

### Post by Extr3me on 2006-11-30
OK, I haven't been able to discover a fix for Rhythmbox dropping the OGG vorbis streamed feed every time the song name is published to the stream, but I have found an easier work-a-round.

Basically, just install XMMS and it allows direct control over the OGG Vorbis streaming plugin!  It will let you adjust the buffer size, and doesn't bother with the song notification, therefore letting you to listen to your internet feed all day long.

Thank god, the office without the radio sucks.

But, I spent a bit of time installing a pile of debug packages for Rhythmbox, GStreamer and the codecs. So if anyone has any idea how to obtain a trace of the program during execution (when it doesn't actually bomb) would be appreciated so I could post it to the Ubuntu bug site.

Thanks and good luck with your own favourite streams (and watch out for the boss)...

---

### Post by Mau on 2006-12-03
Has anyone figured this out for rhythmbox?  I would rather use rhythmbox,  but I experience this too for radio stations.  When the feed stops working, I get "Internel error."

---

### Post by Iusedtowearatie on 2006-12-17
Problem still unsolved? I have had the exact same problem, and would really like to get this working - with RhythmBox. Sorry to see the thread sinking deeper...

---

