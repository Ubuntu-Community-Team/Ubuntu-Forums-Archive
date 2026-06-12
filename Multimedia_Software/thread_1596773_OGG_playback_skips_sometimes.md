---
title: "OGG playback skips sometimes"
date: 2010-10-14
forum: Multimedia Software
---

### Post by nLinked on 2010-10-14
Ubuntu 10.10 all updated.

I have some OGG music. After every 10-20 seconds of playback in Rhythmbox, VLC or Totem, the music will pause and go silent for a second or two before resuming, and this repeats every 10-20 seconds. It also happens at the same points across the track each time I play the song in any of these players.

But if I put the song in Audacity or MPlayer, it plays fine.

I ran VLC from the terminal, and as it played, it returned this error in the terminal window every time the skipping happened every 10-20 seconds:

[0xb32008e4] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 300 ms).

The OGG songs are being played locally, not over a network. What can I do? Only OGG is affected.

---

