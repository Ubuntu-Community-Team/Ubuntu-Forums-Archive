---
title: "Swapping Audio Streams in OGV"
date: 2011-01-06
forum: Multimedia Software
---

### Post by verevie on 2011-01-06
I have a ogg video file of a DVD I backed up with Thoggen. The movie has 2 languages (English and Spanish) and I told it to rip All Languages. However, it ripped the Spanish as Track 1 and English as Track 2. So the default language that the video starts playing in is Spanish (since it's Track 1). Is there a way that I can swap the Vorbis streams and make the English track Track 1 and the Spanish track Track 2?

---

### Post by verevie on 2011-01-06
Bump

---

### Post by BicyclerBoy on 2011-01-06
Should be able to feed thru' ffmpeg with options -vcodec copy -acodec copy & use of the -map 0:0  -map 2:0  -map 1:0

This would swap streams 1 & 2.

First you need to check the stream order reported by ffprobe or ffmpeg.

I'm not sure the standard *buntu ffmpeg package has libtheora & libvorbis enabled...
It will report this when you run ffmpeg..

---

### Post by verevie on 2011-01-07
> **BicyclerBoy said:**
> Should be able to feed thru' ffmpeg with options -vcodec copy -acodec copy & use of the -map 0:0  -map 2:0  -map 1:0

This would swap streams 1 & 2.

First you need to check the stream order reported by ffprobe or ffmpeg.

I'm not sure the standard *buntu ffmpeg package has libtheora & libvorbis enabled...
It will report this when you run ffmpeg..
Mint does, so I would assume Ubuntu enables it. Thanks. I knew about "copy" but not about -map. Thanks. :D

---

### Post by ron999 on 2011-01-07
Hi
I realize that the thread is marked 'SOLVED', but I think this is the way to map those streams:-
```
ffmpeg -i input.ogv -map 0:0 -map 0:2 -vcodec copy -acodec copy output.ogv -map 0:1 -acodec copy -newaudio
```

---

### Post by BicyclerBoy on 2011-01-07
I wasn't game to post a working ffmpeg command..
They never work 1st or 2nd time...

Best I could do was suggest an approach..

---

### Post by verevie on 2011-01-09
> **ron999 said:**
> Hi
I realize that the thread is marked 'SOLVED', but I think this is the way to map those streams:-
```
ffmpeg -i input.ogv -map 0:0 -map 0:2 -vcodec copy -acodec copy output.ogv -map 0:1 -acodec copy -newaudio
```
For some reason, ffmpeg doesn't play well with Vorbis and (at least on my computer) the output audio skips.
```
oggz-rip -c theora input.ogv > inputnoaudio.ogv
ogmdemux input.ogv 
oggz-merge -o output.ogv inputnoaudio.ogv input.ogv-a2.ogg input.ogv-a1.ogg 

```
seems to work for me. Just another way to do it. Hope this helps other people. :)

---

### Post by BicyclerBoy on 2011-01-09
Good for you..
Always another way..

The ffmpeg in Ubuntu does not have libtheora or libvorbis included.
So ffmpeg may not have worked anyway.

Might have needed multiverse & universe repos & libavformat52-extras.
And still needed to built from source !

---

