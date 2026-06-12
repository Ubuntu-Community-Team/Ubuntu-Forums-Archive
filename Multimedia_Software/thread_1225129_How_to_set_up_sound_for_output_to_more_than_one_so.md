---
title: "How to set up sound for output to more than one soundcard?"
date: 2009-07-28
forum: Multimedia Software
---

### Post by mikeym on 2009-07-28
I was wanting to set up a few sound cards for simultaneous output to different speakers in different rooms. From what I've read it seems that pulse audio would be the program for this but how would I go about it?

In an ideal world I would be able to output from different applications into different rooms or from one program into more than one room. For example if this would involve a wrapper script then something like:

```

outputto room1 mpg123 "Add Insult to Injury - 07 - Add N to (X) - Plug Me In.mp3"
outputto room1 room2 mplayer -cache-min 4 -playlist http://www.bbc.co.uk/iplayer/aod/playlists/9p/gv/l0/0b/RadioBridge_uk_0800_bbc_6music.ram

```

---

