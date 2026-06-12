---
title: "Rosegarden audio output"
date: 2007-05-12
forum: Multimedia &amp; Video
---

### Post by homer.s on 2007-05-12
I've installed timidity and a bunch of other packages so that I can play midi files, and it works fine when I paly midi with timidity on the konsole.  When I try to play the same midi file on rosegarden, however, there is no sound output, it gave me a warning about my system timer resolution being too low instead.   I tried to get linux-realtime to solve the problem but it only got rid of the warning message and did nothing to enable midi playback, it also ruined my wireless configuration so I had to get rid of it.

I tried to run "timidity -iA -B2,8 -Os" before I started timidity and the audio worked, but I'm looking a permanant fix and I'm too lazy to remember to do a command every time I want to listen to "Super Mario Bros.".

I'm running the latest version of Kubuntu and I use an Inspiron B2120.

---

### Post by oliwally on 2007-05-15
I've go the same problem. Installed the lowlatency kernel, but getting no sound out of Rosegarden. How is it done?

---

### Post by aonegodman on 2007-12-26
Nobody seems to have a REAL fix to these problems surrounding Rosegarden - Timidity - Jack and Midi ect.

I am searching for many of the same answers as everyone else on the forum.

I did find one solution to those of us who have a strong interest in these programs and the audio recording side of things. It's called **Studio To Go** and it is a packaged distro based on KDE. I d/l'd the demo ISO and burned it and stuck it in my laptop and it fired up the first time with Rosegarden, Jack and all the crew and played great.

I know it can work but looks like the folks at "Studio To Go" are the only ones who know how.  It will cost ya about $169US to bypass all this tweaking.

Run a search for Studio To Go.

---

