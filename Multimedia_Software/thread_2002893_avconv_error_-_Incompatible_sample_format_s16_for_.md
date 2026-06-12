---
title: "avconv error - Incompatible sample format s16 for codec ac3"
date: 2012-06-13
forum: Multimedia Software
---

### Post by nhtrader on 2012-06-13
mythbuntu 12.04 64bit
ffmpeg or avconv version 0.8.1-4:0.8.1-0ubuntu1, Copyright (c) 2000-2011 the Libav developers, built on Mar 22 2012 05:09:06 with gcc 4.6.3


I upgraded my system from mythbuntu 10.10 64bit to 12.04 64bit and now I can't extract audio from videos. Now I get an error msg ...

Here's the command:
```

avconv -i myshow.mpg -vn -ar 48000 -acodec ac3 -ac 2 -ab 192k -f mp3 U2012061200.mp3

```

Here's the response:
```

avconv version 0.8.1-4:0.8.1-0ubuntu1, Copyright (c) 2000-2011 the Libav developers
  built on Mar 22 2012 05:09:06 with gcc 4.6.3
[mpegts @ 0x1fb77a0] Continuity check failed for pid 0 expected 12 got 13
[mpegts @ 0x1fb77a0] max_analyze_duration reached
[mpegts @ 0x1fb77a0] PES packet size mismatch
Input #0, mpegts, from 'myshow.mpg':
  Duration: 01:01:11.06, start: 53829.757900, bitrate: 3038 kb/s
  Program 1 
    Stream #0.0[0xf91]: Video: mpeg2video (Main), yuv420p, 528x480 [PAR 40:33 DAR 4:3], 7000 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0xf92](eng): Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
Incompatible sample format 's16' for codec 'ac3', auto-selecting format 'flt'
Output #0, mp3, to 'U2012061200.mp3':
  Metadata:
    TSSE            : Lavf53.21.0
    Stream #0.0(eng): Audio: ac3, 48000 Hz, stereo, flt, 192 kb/s
Stream mapping:
  Stream #0:1 -> #0:0 (ac3 -> ac3)
Press ctrl-c to stop encoding
[mpegts @ 0x1fb77a0] Continuity check failed for pid 0 expected 12 got 13
Input stream #0:1 frame changed from rate:48000 fmt:s16 ch:2 to rate:48000 fmt:flt ch:2
Continuity check failed for pid 3985 expected 15 got 0
Continuity check failed for pid 3985 expected 11 got 13
[mpegts @ 0x1fb77a0] Continuity check failed for pid 3985 expected 14 got 15
PES packet size mismatch5.33 bitrate= 192.0kbits/s    
[ac3 @ 0x1fbed40] incomplete frame
size=   86039kB time=3670.98 bitrate= 192.0kbits/s    
video:0kB audio:86038kB global headers:0kB muxing overhead 0.000146%


```

The resulting *.mp3 file is 84Mb is size but when opened in "audacity" it only represents 1 second of audio. It should be 1 hour.

Has anyone solved this?

---

### Post by ron999 on 2012-06-13
> **nhtrader said:**
> 
Has anyone solved this?
Hi
Use this command to install the codecs:-
```
sudo apt-get install libavcodec-extra-53
```

Then you can extract audio from videos like this:-
```
ffmpeg -i myshow.mpg -acodec libmp3lame -ab 192k -ac 2 -ar 44100 U2012061200.mp3
```

---

### Post by nhtrader on 2012-06-14
> **ron999 said:**
> Hi
Use this command to install the codecs:-
```
sudo apt-get install libavcodec-extra-53
```

Then you can extract audio from videos like this:-
```
ffmpeg -i myshow.mpg -acodec libmp3lame -ab 192k -ac 2 -ar 44100 U2012061200.mp3
```

Fantastic. This worked. I was able to extract the audio. Thank you. I can now edit it using Audacity.

But I have to say that I wasn't optimistic as it was decoding b/c of the following output:
```

 avconv -i "myshow.mpg" -vn -acodec libmp3lame -ar 44100 -map 0:1 -ac 2 -ab 192k -f mp3 U20120612.mp3
avconv version 0.8.1-4:0.8.1-0ubuntu1, Copyright (c) 2000-2011 the Libav developers
  built on Mar 22 2012 05:09:06 with gcc 4.6.3
[mpegts @ 0x6f89c0] max_analyze_duration reached
[mpegts @ 0x6f89c0] PES packet size mismatch
Input #0, mpegts, from 'myshow.mpg':
  Duration: 01:00:58.40, start: 23763.006678, bitrate: 2806 kb/s
  Program 1 
    Stream #0.0[0xf51]: Video: mpeg2video (Main), yuv420p, 704x480 [PAR 10:11 DAR 4:3], 15000 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0xf52](eng): Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
    Stream #0.2[0xf53](eng): Audio: ac3, 48000 Hz, mono, s16, 128 kb/s
Output #0, mp3, to 'U20120612.mp3':
  Metadata:
    TSSE            : Lavf53.21.0
    Stream #0.0(eng): Audio: libmp3lame, 44100 Hz, stereo, s16, 192 kb/s
Stream mapping:
  Stream #0:1 -> #0:0 (ac3 -> libmp3lame)
Press ctrl-c to stop encoding
Continuity check failed for pid 3921 expected 2 got 3
Continuity check failed for pid 3921 expected 7 got 9
[mpegts @ 0x6f89c0] Continuity check failed for pid 3921 expected 11 got 12
[mpegts @ 0x6f89c0] Continuity check failed for pid 3922 expected 11 got 12
[mpegts @ 0x6f89c0] PES packet size mismatch
[ac3 @ 0x6fff60] frame CRC mismatch
[ac3 @ 0x6fff60] frame sync error
Error while decoding stream #0:1
Continuity check failed for pid 3921 expected 8 got 9 
Continuity check failed for pid 3921 expected 12 got 13
Continuity check failed for pid 3921 expected 7 got 8 
Continuity check failed for pid 3921 expected 12 got 13
PES packet size mismatch7.69 bitrate= 192.0kbits/s    
size=   85729kB time=3657.77 bitrate= 192.0kbits/s    
video:0kB audio:85729kB global headers:0kB muxing overhead 0.000156%


```

But, despite these errors noted, the mp3 plays perfectly.

Thanks again.

---

