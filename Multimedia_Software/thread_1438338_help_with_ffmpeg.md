---
title: "help with ffmpeg"
date: 2010-03-24
forum: Multimedia Software
---

### Post by Dimoutlook on 2010-03-24
Hi to all I've discovered ubuntu's secret weapon for video conversion but I still don't understand what some of the out put means? here is some sample code

ffmpeg -i xxxxxx.avi -target ntsc-dvd -r 29.97 -s 608x336 -padtop 72 -padbottom 72 -padleft 56 -padright 56 xxxxxx.mpg

makes a great dvd complaint mpg

This is the initial ffmpeg -i xxxxxx.avi

 [NULL @ 0xf0c260]Invalid and inefficient vfw-avi packed B frames detected
Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (24000/1001)
Input #0, avi, from 'xxxxx.avi':
Duration: 01:28:09.95, start: 0.000000, bitrate: 1100 kb/s
Stream #0.0: Video: mpeg4, yuv420p, 608x336 [PAR 1:1 DAR 38:21], 23.98 tbr, 23.98 tbn, 23.98 tbc
Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s

now the ffmpeg -i for the finished .mpg

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 29.97 (30000/1001)
Input #0, mpeg, from 'xxxxxx.mpg':
Duration: 01:28:09.88, start: 0.500000, bitrate: 3803 kb/s
Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 32:27 DAR 16:9], 9000 kb/s, 29.97 tbr, 90k tbn, 59.94 tbc
Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, s16, 448 kb/s

Now my question is how did the video change to 720x480 [PAR 32:27 DAR 16:9]
I've noticed that some of the video is wider than the size of 720x480
I have a standard 4:3 tv should this be a concern or just part of the conversion process I'm still learning at age 63 so if I can do this the younger peps should have no problems at all!

Thanks to all who reply 
Dimoutlook

---

### Post by Chronon on 2010-03-25
If you would rather use a GUI, WinFF provides a decent front end to ffmpeg.  It has presets for converting to DVD as well as to various formats used on portable media players and such.

With regard to the dimension, it seems that you're padding the starting width of 608 pixels by 56 pixels on the left and the right.  608 pixels + 112 pixels = 720 pixels.  The height of 336 pixels gets padded by 72 pixels on the bottom and the top.  336 pixels + 144 pixels = 480 pixels.

---

### Post by Dimoutlook on 2010-03-25
Thanks for the info on winff will see what it can do

Dimoutlook

---

