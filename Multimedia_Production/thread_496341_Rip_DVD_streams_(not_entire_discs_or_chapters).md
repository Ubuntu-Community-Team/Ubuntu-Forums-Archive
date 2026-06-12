---
title: "Rip DVD streams (not entire discs or chapters)"
date: 2007-07-09
forum: Multimedia Production
---

### Post by guitard00d on 2007-07-09
I know this has to be possible, because you see all kinds of videos on YouTube and MySpace where a person rips just part of a DVD, not an entire disc or entire chapter. Exactly what program(s) does a person use to capture just a partial segment from a DVD and save it to something like an MPEG file?

I have a bunch of DVDs of bands that I played in (recorded to a set-top DVD recorder from a VHS player) and I want to pick out just specific songs to put on to another DVD using the DeeVeeDee program. My kids want a DVD so they can see me back in my band days (when I still had hair) and there are some of those moments on the videos that I would rather them not see or hear.

If anybody can help me here, I would sure appreciate it.

---

### Post by roynux on 2007-07-09
Hello,

You can use mencoder with the -ss and -endpos parameters :
mencoder -oac copy -ovc copy -of mpeg -o myvid1.mpg dvd:// -ss 00:10:00 -endpos 03:05

But I would rip the entire chapter with the song you want, then using ProjectX
[http://www.doom9.org/index.html?/DigiTV/projectx.htm](http://www.doom9.org/index.html?/DigiTV/projectx.htm)
I would cut and demux the interesting sections and remux them with 
```
mplex -f 8 -o myvid.mpeg video_file audio_file
```

This will give you good sync between the audio and the video.

---

