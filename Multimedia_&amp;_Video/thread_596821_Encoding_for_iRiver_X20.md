---
title: "Encoding for iRiver X20"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by andrew.46 on 2007-10-29
Hi,

I have been trying to encode dvd titles to xvid for an iRiver X20 media player with reasonable success. I was hoping however for some expert advice on the technique I have been using as I am a total noob at video encoding and the iRiver X20 is a little fussy about its video.

The iRiver X20 has the following specifications for video playback:

```
Format: xvid
Screen: 320 x 240
fps: 15-30
Video bitrate: 32-512kbps
Audio Bit rate:8-320kbps
```

To do the encoding I am using MEncoder dev-SVN-r24845-4.1.2 and xVid 1.1.3. I have used double pass encoding as follows:

**First pass:**

```
mencoder -v \
        dvd://6 -chapter 6-8 -alang zh \
       -ovc xvid -xvidencopts pass=1:bitrate=512:max_bframes=0 \
       -vf scale=320:240,expand=320:240,harddup \
       -ofps 30 \
       -oac mp3lame -lameopts mode=0:cbr:br=128 \
       -af resample=44100:1:2 \
       -o /dev/null
```

**Second Pass**:

```
mencoder -v \
        dvd://6 -chapter 6-8 -alang zh \
       -ovc xvid -xvidencopts pass=2:bitrate=512:max_bframes=0 \
       -vf scale=320:240,expand=320:240,harddup \
       -ofps 30 \
       -oac mp3lame -lameopts mode=0:cbr:br=128 \
       -af resample=44100:1:2 \
       -o Fist_of_Fury.avi
```

This is a fight scene from Bruce Lee's 'Fist of Fury' so I could see some rapid action. Video looks ok, sound appears to have a bit of an echo and is a little quiet. I tried to add english subtitles but this was a little poor on such a small screen.

Any thoughts, suggestions for improvements?

Andrew

---

