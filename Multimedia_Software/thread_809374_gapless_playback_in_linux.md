---
title: "gapless playback in linux"
date: 2008-05-27
forum: Multimedia Software
---

### Post by BetterSense on 2008-05-27
I'm still trying to settle on music software. I would prefer to use mplayer because I like its audio filters and that's what I use for movies anyway. However it seems that it won't play back FLAC files gaplessly. Rhythmbox also fails to play back gaplessly, although I tested it with ogg. Is there any way to implement proper playback of .flac files in mplayer?

---

### Post by tempel on 2008-05-27
I can't tell you about mplayer, but i have found that it can be fixed in Rhythmbox.  You just need to enable the crossfade plugin and set crossfade time to zero seconds.

---

### Post by BetterSense on 2008-05-27
I was reading the hydrogenaudio wiki about gapless playback and it says that all lossless file formats are inherently gapless. But mplayer clearly inserts gaps when it plays back an album. Does this have something to do with how I tell mplayer to play? I usually cd into an album directory, which has all the album's songs in it in flac format, and then just 

```
mplayer -ao alsa:device=spdif -af pan:2:1:.1:.1:1 *
```

maybe there's some way to tell it to play all the tracks as one file?

---

### Post by BetterSense on 2008-05-29
Everything I read on the hydrogenaudio wiki says that lossless files are inherently gapless, and that mplayer plays flacs gaplessly. But I downloaded the gapless test track from the hydrogenaudio wiki and played it back with mplayer and it very clearly failes the gapless test. Is my mplayer different, or compiled differently from everyone elses?

---

### Post by benow on 2010-01-03
Yo.

It's possible to get gapless working with mplayer using a fifo.

From [here]("http://snipplr.com/view/18353/gapless-playback-for-mplayer-linux/"):

      mkfifo aufifo
      aplay -t raw -c 2 -f S16_LE -r 44100 aufifo &> /tmp/aplayfifo.log &
      gmplayer -ao pcm:nowaveheader:file=aufifo track01.ogg track02.ogg track03.ogg &

---

