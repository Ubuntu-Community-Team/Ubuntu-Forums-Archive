---
title: "alternative to handbrake? to convert video to mpg4"
date: 2011-08-13
forum: Multimedia Software
---

### Post by chris1497 on 2011-08-13
I'm currently using handbrake (with the gui) to convert some video files to mpg4.  It takes about 2 hours to convert an average movie is there anything a little speedier? I'm running a core2duo processor.  

file types:
.vob ----> .m4v

I'm also open to cli suggestions.

---

### Post by papibe on 2011-08-13
If you don't have problems using the terminal, you should try ffmpeg. Here's a [youtube]("http://www.youtube.com/watch?v=iIalNEW-LQ8") tutorial.

Regards.

---

### Post by chris1497 on 2011-08-13
Thanks for the response.  I looked into ffmpeg before, but couldn't seem to get it to work, despite looking at a few different tutorials.

The tutorial doesn't explain what the video container is? 

here is my attempt:

```
ffmpeg -i MOVIE.VOB -vcodec vob -sameq MOVIE_FINAL.mp4
```

```
Seems stream 0 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 59.94 (60000/1001)
Input #0, mpeg, from 'WAR.VOB':
  Duration: 01:42:58.84, start: 89.539733, bitrate: 5528 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 32:27 DAR 16:9], 9800 kb/s, 23.98 fps, 59.94 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x80]: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
    Stream #0.2[0x81]: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
    Stream #0.3[0x82]: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
    Stream #0.4[0x83]: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
    Stream #0.5[0x84]: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
Unknown encoder 'vob'
```

---

### Post by chris1497 on 2011-08-13
clearly I'm messing up something with the audio

tried this:

```
ffmpeg -i WAR.VOB -acodec ac3 -sameq output.mp4
```
There is a lot of output, but these arein red and seem bad:

[ac3 @ 0x157c710]frame sync error

Bit allocation failed. Try increasing the bitrate.

---

