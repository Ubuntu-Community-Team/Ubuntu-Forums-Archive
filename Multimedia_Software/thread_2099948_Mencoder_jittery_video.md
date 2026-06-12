---
title: "Mencoder jittery video"
date: 2012-12-31
forum: Multimedia Software
---

### Post by tsumaru on 2012-12-31
Hi all

Just looking to get some advice from some mencoder gurus.

I have a video that is using a codec that my Phone doesnt like, avc1 i believe.

I am trying to use mencoder to convert it to x264.
I have it converting fine(tm) however i have noticed that some of the scenes are a little jerky. Its a Disney film and the most noticable part is the disney bit at the beginning with the castle.

I can confirm the original video does NOT have this problem.

Original video is 23.976 FPS and that is what mencoder is using when it transcodes.

The following command is what i am using:

```
mencoder -idx -o "/home/simon/Brave_phone.mkv" -aid 0 -ovc x264 -x264encopts bitrate=3000:keyint=250:me=umh:me_range=4:subq=5:threads=auto -oac mp3lame -lameopts cbr:br=128 /home/simon/Brave.mkv
```

The "me=umh:me_range=4:subq=5" is me playing to try to fix this problem as i thought it might be an issue with motion estimation but every iteration of those three commands doesnt seem to fix my problem

Anyone got any ideas?

---

### Post by evilsoup on 2012-12-31
You might consider using ffmpeg, or avconv, the fork of ffmpeg in the Ubuntu repositories, instead. [Here](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide) is a guide to encoding videos using x264 with ffmpeg (if you use avconv, the syntax is the same, just replace every instance of 'ffmpeg' with 'avconv'). AFAIK, mencoder isn't actively developed any more, whereas ffmpeg is, so you might have more luck with it.

---

### Post by tsumaru on 2012-12-31
As it happens i just managed to resolve this no more than 5 minutes ago

using the following eliminated the jittering i was experiencing but i found that it wouldnt play on my phone so i have also made it output in mp4 format.

The following works:

```
mencoder -idx -o "/home/simon/Brave_phone.mkv" -aid 0 -ovc x264 -x264encopts bitrate=3000:keyint=250:no8x8dct:bframes=0:nocabac:trellis=0:nomixed-refs:global_header:threads=auto -oac mp3lame -lameopts cbr:br=128 -of lavf -lavfopts format=mp4 /home/simon/Brave.mkv
```

For clarification, The goal was to have this play using hardware decoding on my Nexus 4. (Software decoding on it was rubbish!)

---

