---
title: "Rosegarden: midi instrument selection incorrect"
date: 2008-01-14
forum: Multimedia &amp; Video
---

### Post by gratefulfrog on 2008-01-14
First, let me say that this is my first attempt to play with Midi stuff on Linux. Until now, it was my son who did this on Windows, and we are trying to set up an equivalent tool set on Linux. 

Please forgive any stupid things I may say due to lack of understanding about midi, jack, or all their friends.

I have installed rosegarden, jack, timidity, and lots of other things. it seems that rosegarden has found timidity somehow and is using that to play through. I ran this command to get sound:

$ timidity -iA -B2,8 -Os

1. I have a test mdi file: "Baker Street" which I can play perfectly on XMMS. All the instruments are correctly assigned and it plays smoothly.

2. I start. Rosegarden, which I have configured to start jack. This looks good. Rosegarden example "rg" files load a play correctly.
3. I load the midi file, which imports.
4. Here's the problem: The instrument assignments seem to be "lost". rosegarden seems to select some kind of default config:
I see for all the tracks except the last one (track 10):
Track Parameters:
Device: General Midi
Instrument: #1 (Acoustic Grand Piano)

Instrument Parameters:
Channel Out: 1
Program  : 1. Acoustic Grand Piano

The last one differs in that:
Channel out: 10
Percussion:  (selected)

So my question is: Does anyone know how to get the correct instrument assignments to work on import?

---

