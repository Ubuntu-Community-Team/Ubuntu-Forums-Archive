---
title: "Any tools to determine AVI file attributes?"
date: 2006-10-10
forum: Multimedia &amp; Video
---

### Post by grahams on 2006-10-10
I'd like to be able to see the attributes of AVI files beyond what I can see with 'file' or stream info from xine. Are there any tools that can show video bitrates, tags, codecs etc.

much gracias :)

---

### Post by kuja on 2006-10-10
One thing you could do is to play the file in mplayer from a terminal, that will show you some useful information.

---

### Post by bruenig on 2006-10-10
generally doing
```
file whatever.avi
```
will display a lot of what you mentioned.

---

### Post by grahams on 2006-10-11
Thanks for the replies. 

I'm looking for more info than file, mplayer or xine are able to provide. 

I find some avi files will not play on my dvd player correctly. It's likely the video bitrate is too high, but I haven't found a way to display this level of info. If I convert the avi with avidemux with a bitrate I know works the file plays perfectly. However file original.avi & file converted.avi show the same basic info even thought they are clearly now different.

In the windoze world I believe virtual dub shows this detail.

---

### Post by lokalhost on 2006-10-11
Transcode comes with a tool: tcprobe Might do what you're after

Sample:

```

[ 16:44:37 | dvr | ~ ]
 :: tcprobe -i /var/www/html/apple.avi
[tcprobe] RIFF data, AVI video
[avilib] V: 29.970 fps, codec=DX50, frames=6235, width=336, height=220
[avilib] A: 11025 Hz, format=0x55, bits=0, channels=1, bitrate=19 kbps,
[avilib]    3974 chunks, 517920 bytes, CBR
[tcprobe] summary for /var/www/html/apple.avi, (*) = not default, 0 = not detected
import frame size: -g 336x220 [720x576] (*)
       frame rate: -f 29.970 [25.000] frc=4 (*)
      audio track: -a 0 [0] -e 11025,0,1 [48000,16,2] -n 0x55 [0x2000] (*)
                   bitrate=19 kbps
           length: 6235 frames, frame_time=33 msec, duration=0:03:28.041


```

---

### Post by grahams on 2006-12-22
I did a little more research and I don't think we have a tool in Linux to show the details I'm looking for. tcprobe & file etc. will show the basic info on codec's but my dvd (philips 642) player is fussy and doesn't like xvid4 etc. Tools like gspot (windoze only), give more detail.

---

