---
title: "MPD/Sonata errors linked to Firefox/Swiftfox/etc?"
date: 2008-03-17
forum: Multimedia &amp; Video
---

### Post by SomeGuyDude on 2008-03-17
This is the goofiest problem I've seen in a while, maybe someone can explain it.

Every so often Sonata will stop playing, telling me it's "Not Connected". This happens randomly, often I don't realize it's stopped for a little while so I can't say exactly what triggers it.

Running Sonata from the terminal gives me a timeout on connecting to MPD, and MPD itself becomes unresponsive.

Now, and here's the strange part, if I close Swiftfox, it starts again and everything's fine! Then I start SF and all problems are gone. I had to do it about five minutes ago. MPD stopped, I closed Swiftfox, my music started playing again on its own, and restarted my browser.

Is there anything I can look for to explain where this conflict is?

---

### Post by aidanr on 2008-03-17
Are you using any plugins in switfox when it crashes mpd? Maybe try changing mpd's audio output (see /etc/mpd.conf for how to do this and put it in ~/.mpdconf).

---

### Post by SomeGuyDude on 2008-03-18
Quite a few, yes.

At first I thought it was linked to YouTube because once it crapped out while a video was playing, but it wasn't consistant nor the only time it happened. Might look into messing with audio outputs. I'll try that out tomorrow.

---

