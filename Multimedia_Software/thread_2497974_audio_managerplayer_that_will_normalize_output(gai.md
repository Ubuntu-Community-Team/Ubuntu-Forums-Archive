---
title: "audio manager/player that will normalize output(gain)?"
date: 2024-05-24
forum: Multimedia Software
---

### Post by schwim-dandy on 2024-05-24
Hello there, everyone!

If Rhythmbox can do it, I can't find the setting for it.  I have some playlists that I use to play along with on guitar and drums and over the years, my ripping of audio has had various levels of volume applied.  A very long time ago, I used a music player(Songbird or the fork, IIRC) to attain similar levels of output but I'm having a problem finding an audio player for local media that can do the same.

Any help would be greatly appreciated.  Thanks for your time!

---

### Post by #&amp;thj^% on 2024-05-24
I wonder if this might help:
```
 apt search normalize-audio
normalize-audio/oracular 0.7.7-18 amd64
  adjusts the volume of WAV, MP3 and OGG files to a standard volume level

```
A small learning curve as with anything new:
```
]]$ normalize-ogg sample.ogg
Decoding sample.ogg...
Running normalize...
Re-encoding sample.ogg...
```
it also supports batch processing. So,you could normalize a bunch of audio files:

```
$ normalize-ogg *.ogg
```
There are others as well. 
1.  rgain3 that is written in python
2. mp3gain {in the repos}
3.SoX {Also in the repos}

---

### Post by 909mjolnir on 2024-06-07
One of the older editions of Foobar2000 is not yet damaged by messing things up with ReplayGain (it can be disabled).  
With Foobar2000, there's an add-on that allows VST effects to be used on the outgoing audio.  Look for VST.  
I used to use it during the 32-bit years.

---

