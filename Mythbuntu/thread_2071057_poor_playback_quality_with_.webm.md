---
title: "poor playback quality with *.webm"
date: 2012-10-14
forum: Mythbuntu
---

### Post by nhtrader on 2012-10-14
I am experimenting with *.webm videos. I've created several *.webm videos using different bit rates and in all cases the playback quality in MythTV FE is poor - highly pixelated. However, when viewing the same videos using VLC player, these videos appear much better (some slight/occasional digital artifacts are apparent but not enough to ruin the viewing experience).

I'll admit that my settings to create *.webm are not yet optimized using avconv, but again, VLC plays the videos I've created just fine.

Why does the playback quality of *.webm depend on the player? 
Why are there noticeable differences among players? 
Why is MythTV's player so different?

---

### Post by nickrout on 2012-10-14
> **nhtrader said:**
> I am experimenting with *.webm videos. I've created several *.webm videos using different bit rates and in all cases the playback quality in MythTV FE is poor - highly pixelated. However, when viewing the same videos using VLC player, these videos appear much better (some slight/occasional digital artifacts are apparent but not enough to ruin the viewing experience).

I'll admit that my settings to create *.webm are not yet optimized using avconv, but again, VLC plays the videos I've created just fine.

Why does the playback quality of *.webm depend on the player? 
Why are there noticeable differences among players? 
Why is MythTV's player so different?To get the Internal player improved you need to create a ticket in trac and make a sample of the offending video available to the developers.

EDIT: [http://code.mythtv.org/trac/wiki/TicketHowTo](http://code.mythtv.org/trac/wiki/TicketHowTo)

As to the difference between players, well I am not familiar with the code, but you can of course look for yourself :)

---

