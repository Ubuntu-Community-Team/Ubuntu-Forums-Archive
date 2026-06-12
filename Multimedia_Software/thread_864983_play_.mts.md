---
title: "play .mts"
date: 2008-07-20
forum: Multimedia Software
---

### Post by milanvora2 on 2008-07-20
i have a sony tg1 camera which creates .mts files.
i tried to play them under vlc, but it hangs up after a second.
if i play them under mplayer i get the sound but no video.
any clues how i could play them ?
thanks in advance

---

### Post by xc3RnbFO8P on 2008-07-20
Read this:
[http://www.fsckin.com/2008/01/03/transcoding-mtsm2ts-avchd-video-files-with-free-software/]("http://www.fsckin.com/2008/01/03/transcoding-mtsm2ts-avchd-video-files-with-free-software/")
May this is easier:
[http://wesleybailey.com/articles/m2tstoavi-avchd]("http://wesleybailey.com/articles/m2tstoavi-avchd")

---

### Post by milanvora2 on 2008-07-22
followed instructions. but i don't need to convert the fiels. i just want to play them.

compiled fresh x264 & ffmpeg, but still no results

vlc still crashes when playing the mts files.

does anyone know any other way ?

---

### Post by firsttimeuser on 2009-09-07
i have the same problem, does anyone have any answer for this at this time?

---

### Post by andrew.46 on 2009-09-07
Hi firsttimeuser,

> **firsttimeuser said:**
> i have the same problem, does anyone have any answer for this at this time?

I will admit to next to no knowledge of this format except to know that some cameras generate it, but I believe that the svn MPlayer will play the files with no problem. I tested on this large file:

```
wget http://samples.mplayerhq.hu/archive/extension/mts/mpegts+h264+ac3++canon-hg10-avchd-1080-50i-plays-half-speed.mts
```

This file is a little damaged, which is what it is doing on the MPlayer 'samples' site, but it was the only sample I could find :-). I attach a screenshot of the svn MPlayer playing it.

All the best,

Andrew

---

### Post by mcduck on 2009-09-08
The format is MPEG Transport Stream, and it's not very commonly supported by media players.

The good thing, though, is that converting from transport stream to normal MPEG Program Stream file doesn't require re-ecoding the actual video material, so it's very quickly done and wwon't reduce the quality if you can find a program that does the job.

I use MPEG Streamclip to convert from transport stream to normal files, but that's OSX app.. But I bet that VLC would able to play the files, and most likely also would convert them to normal program stream files if you just figure out the command.. :)

[http://en.wikipedia.org/wiki/MPEG_transport_stream]("http://en.wikipedia.org/wiki/MPEG_transport_stream")

---

