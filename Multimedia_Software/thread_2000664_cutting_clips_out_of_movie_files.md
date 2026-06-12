---
title: "cutting clips out of movie files"
date: 2012-06-09
forum: Multimedia Software
---

### Post by Andrew Golightly on 2012-06-09
Hi all,

So from this page: [http://askubuntu.com/questions/59383/extract-part-of-a-video-with-a-one-line-command](http://askubuntu.com/questions/59383/extract-part-of-a-video-with-a-one-line-command)

I'm trying this command: ffmpeg -vcodec copy -acodec copy -i orginalfile -ss 00:00:30 -t 00:00:05 newfile

When running it on a m4v file (created by Handbrake) the audio and video is out of sync. Is there a sure fire format to make sure it works? Ultimately we'll be uploading clips of the video to YouTube for work.

thanks!

---

### Post by shantiq on 2012-06-10
hi Andrew i have found this too often with ffmpeg


av a read [**here**]("http://ubuntuforums.org/showthread.php?t=1782270").   Using mencoder has always given me better results  [no av sync probs]



specifically this line [but i suggest to read full info for details]


> mencoder  -ss 01:00:00  -endpos 00:05:56 -oac copy -ovc copy input.mp4 -o output.mp4

---

### Post by Hari5g900 on 2012-06-10
Why don't you try installing avidemix or pitivi? It always works for me.

---

### Post by Andrew Golightly on 2012-06-10
> **shantiq said:**
> hi Andrew i have found this too often with ffmpeg


av a read [**here**]("http://ubuntuforums.org/showthread.php?t=1782270").   Using mencoder has always given me better results  [no av sync probs]



specifically this line [but i suggest to read full info for details]

I got this error:

> MEncoder svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
Option oac: Unknown suboption mp4
Error parsing option on the command line: -oac

Exiting... (error parsing command line)

---

### Post by Andrew Golightly on 2012-06-10
> **Hari5g900 said:**
> Why don't you try installing avidemix or pitivi? It always works for me.

Pitivi has horrible reviews.. so I installed avidemux. On loading the file I got:

> H.264 detected

If the file is using B-frames as reference it can lead to a crash or stuttering.
Avidemux can use another mode which is safe but YOU WILL LOSE FRAME ACCURACY.
Do you want to use that mode?

On choosing yes, the video and audio seemed out of sync. On choosing no, it crashed.

This is the encoding Handbrake used. I notice I can set the video encoding to be mpeg4 or mpeg2 or vp3.

Basically a client has given me some of her DVDs she has made. Wants me to take clips out and put them on YouTube. It seemed the easiest was to rip using Handbrake and then cut clips using avidemux?

---

### Post by shantiq on 2012-06-10
sorry Andrew    should read 

> mencoder  -ss 01:00:00  -endpos 00:05:56 -**oac copy** -ovc copy input.mp4 -o output.mp4


i have changed it   it might ask you to use pcm instead of copy which bumps up the size but you will see the av is fine      again sorry about mistake:KS



> mencoder  -ss 01:00:00  -endpos 00:05:56 -**oac pcm** -ovc copy input.mp4 -o output.mp4

---

### Post by Andrew Golightly on 2012-06-10
> **shantiq said:**
> sorry Andrew    should read 




i have changed it   it might ask you to use pcm instead of copy which bumps up the size but you will see the av is fine      again sorry about mistake:KS

Thanks Shantiq. Yes, I needed to add pcm for the command to execute. The output doesn't work though.. audio plays at correct pace, and the video looks like someone has it on intermittent fast forward bursts. So I take it I need to encode it as something different to start with now? Or edit the mencoder line to encode with something else?

---

### Post by FakeOutdoorsman on 2012-06-10
> **Andrew Golightly said:**
> Hi all,

So from this page: [http://askubuntu.com/questions/59383/extract-part-of-a-video-with-a-one-line-command](http://askubuntu.com/questions/59383/extract-part-of-a-video-with-a-one-line-command)

I'm trying this command: ffmpeg -vcodec copy -acodec copy -i orginalfile -ss 00:00:30 -t 00:00:05 newfile

When running it on a m4v file (created by Handbrake) the audio and video is out of sync. Is there a sure fire format to make sure it works? Ultimately we'll be uploading clips of the video to YouTube for work.

thanks!

Can you show your actual ffmpeg command and the complete console output?
Are you using 12.04 as your profile states?
What player are you using?
Does the output play normally with ffplay?

Note that options placed before *-i* are intended to be applied to the input; therefore *-vcodec copy -acodec copy* should be placed past *-i input* so it is applied to the output. The version you are using probably is applying these options to the output as you are intending, but this won't work with a newer ffmpeg resulting in *Unknown decoder 'copy'*.

---

### Post by Andrew Golightly on 2012-06-10
> **FakeOutdoorsman said:**
> Can you show your actual ffmpeg command and the complete console output?
Are you using 12.04 as your profile states?
What player are you using?
Does the output play normally with ffplay?

Note that options placed before *-i* are intended to be applied to the input; therefore *-vcodec copy -acodec copy* should be placed past *-i input* so it is applied to the output. The version you are using probably is applying these options to the output as you are intending, but this won't work with a newer ffmpeg resulting in *Unknown decoder 'copy'*.

Sure thing..

> mencoder -ss 00:02:45 -endpos 00:00:15 -oac pcm -ovc copy ~/Desktop/Sohum\ Sai.m4v -o ~/Desktop/mind.mp4

I am using 12.04. I play the videos through VLC and plays just the same through ffplay.

The output is:


```
MEncoder svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team

WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
success: format: 0  data: 0x0 - 0x1ebc8c3b
libavformat version 53.21.0 (external)
Mismatching header version 53.19.0
libavformat file format detected.
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0, -alang und
[lavf] stream 2: audio (ac3), -aid 1, -alang und
VIDEO:  [H264]  720x576  24bpp  100.000 fps  1537.9 kbps (187.7 kbyte/s)
[V] filefmt:44  fourcc:0x34363248  size:720x576  fps:100.000  ftime:=0.0100
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
AUDIO: 48000 Hz, 2 ch, s16le, 160.0 kbit/10.42% (ratio: 19998->192000)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
videocodec: framecopy (720x576 24bpp fourcc=34363248)
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.2s     22f ( 6%)  0.00fps Trem:   0min   6mb  A-V:-0.021 [0:0]

1 duplicate frame(s)!
Pos:   0.3s     32f ( 6%)  0.00fps Trem:   0min   8mb  A-V:-0.021 [0:0]

1 duplicate frame(s)!
Pos:   0.4s     42f ( 6%)  0.00fps Trem:   0min  10mb  A-V:-0.021 [0:0]

1 duplicate frame(s)!
Pos:   0.5s     52f ( 6%)  0.00fps Trem:   0min  13mb  A-V:-0.021 [0:1536]

1 duplicate frame(s)!
Pos:   0.7s     62f ( 6%)  0.00fps Trem:   0min  15mb  A-V:-0.021 [0:1536]

1 duplicate frame(s)!
Pos:   0.8s     72f ( 6%)  0.00fps Trem:   0min  17mb  A-V:-0.021 [0:1536]

1 duplicate frame(s)!
Pos:   0.9s     82f ( 6%)  0.00fps Trem:   0min  20mb  A-V:-0.021 [0:1536]

1 duplicate frame(s)!
Pos:   1.0s     92f ( 6%)  0.00fps Trem:   0min  22mb  A-V:-0.021 [0:1536]

1 duplicate frame(s)!
Pos:   1.1s    102f ( 6%)  0.00fps Trem:   0min  25mb  A-V:-0.021 [10211:1536]

1 duplicate frame(s)!
Pos:   1.2s    112f ( 6%)  0.00fps Trem:   0min  27mb  A-V:-0.021 [10278:1536]

1 duplicate frame(s)!
Pos:   1.3s    122f ( 6%)  0.00fps Trem:   0min  29mb  A-V:-0.021 [10338:1536]

1 duplicate frame(s)!
Pos:   1.4s    132f ( 6%)  0.00fps Trem:   0min  31mb  A-V:-0.021 [10380:1536]

1 duplicate frame(s)!
Pos:   1.5s    142f ( 6%)  0.00fps Trem:   0min  35mb  A-V:-0.021 [10336:1536]

1 duplicate frame(s)!
Pos:   1.6s    152f ( 6%)  0.00fps Trem:   0min  37mb  A-V:-0.021 [10360:1536]

1 duplicate frame(s)!
Pos:   1.8s    162f ( 6%)  0.00fps Trem:   0min  38mb  A-V:-0.021 [10334:1536]

1 duplicate frame(s)!
Pos:   1.9s    172f ( 6%)  0.00fps Trem:   0min  40mb  A-V:-0.021 [10313:1536]

1 duplicate frame(s)!
Pos:   2.0s    182f ( 6%)  0.00fps Trem:   0min  42mb  A-V:-0.021 [10311:1536]

1 duplicate frame(s)!
Pos:   2.1s    192f ( 6%)  0.00fps Trem:   0min  45mb  A-V:-0.021 [10230:1536]

1 duplicate frame(s)!
Pos:   2.2s    202f ( 6%)  0.00fps Trem:   0min  46mb  A-V:-0.021 [10192:1536]

1 duplicate frame(s)!
Pos:   2.3s    212f ( 6%)  0.00fps Trem:   0min  49mb  A-V:-0.021 [10330:1536]

1 duplicate frame(s)!
Pos:   2.4s    222f ( 6%)  0.00fps Trem:   0min  50mb  A-V:-0.021 [10290:1536]

1 duplicate frame(s)!
Pos:   2.5s    232f ( 6%)  0.00fps Trem:   0min  53mb  A-V:-0.021 [10284:1536]

1 duplicate frame(s)!
Pos:   2.6s    242f ( 7%)  0.00fps Trem:   0min  57mb  A-V:-0.021 [10696:1536]

1 duplicate frame(s)!
Pos:   2.7s    252f ( 7%)  0.00fps Trem:   0min  57mb  A-V:-0.021 [10410:1536]

1 duplicate frame(s)!
Pos:   2.9s    262f ( 7%)  0.00fps Trem:   0min  57mb  A-V:-0.021 [10066:1536]

1 duplicate frame(s)!
Pos:   3.0s    272f ( 7%)  0.00fps Trem:   0min  57mb  A-V:-0.021 [9719:1536]]

1 duplicate frame(s)!
Pos:   3.1s    282f ( 7%)  0.00fps Trem:   0min  59mb  A-V:-0.021 [9424:1536]

1 duplicate frame(s)!
Pos:   3.2s    292f ( 7%)  0.00fps Trem:   0min  59mb  A-V:-0.021 [9174:1536]

1 duplicate frame(s)!
Pos:   3.3s    302f ( 7%)  0.00fps Trem:   0min  59mb  A-V:-0.021 [8903:1536]

1 duplicate frame(s)!
Pos:   3.4s    312f ( 7%)  0.00fps Trem:   0min  60mb  A-V:-0.021 [8651:1536]

1 duplicate frame(s)!
Pos:   3.5s    322f ( 7%)  0.00fps Trem:   0min  61mb  A-V:-0.021 [8418:1536]

1 duplicate frame(s)!
Pos:   3.6s    332f ( 7%)  0.00fps Trem:   0min  61mb  A-V:-0.021 [8187:1536]

1 duplicate frame(s)!
Pos:   3.7s    342f ( 7%)  0.00fps Trem:   0min  61mb  A-V:-0.021 [7966:1536]

1 duplicate frame(s)!
Pos:   3.8s    352f ( 7%)  0.00fps Trem:   0min  61mb  A-V:-0.021 [7762:1536]

1 duplicate frame(s)!
Pos:   4.0s    362f ( 7%)  0.00fps Trem:   0min  61mb  A-V:-0.021 [7572:1536]

1 duplicate frame(s)!
Pos:   4.1s    372f ( 7%)  0.00fps Trem:   0min  63mb  A-V:-0.021 [7387:1536]

1 duplicate frame(s)!
Pos:   4.2s    382f ( 7%)  0.00fps Trem:   0min  63mb  A-V:-0.021 [7204:1536]

1 duplicate frame(s)!
Pos:   4.3s    392f ( 7%)  0.00fps Trem:   0min  63mb  A-V:-0.021 [7021:1536]

1 duplicate frame(s)!
Pos:   4.4s    402f ( 7%)  0.00fps Trem:   0min  64mb  A-V:-0.021 [7073:1536]

1 duplicate frame(s)!
Pos:   4.5s    412f ( 7%)  0.00fps Trem:   0min  66mb  A-V:-0.021 [7140:1536]

1 duplicate frame(s)!
Pos:   4.6s    422f ( 7%)  0.00fps Trem:   0min  69mb  A-V:-0.021 [7211:1536]

1 duplicate frame(s)!
Pos:   4.7s    432f ( 7%)  0.00fps Trem:   0min  70mb  A-V:-0.021 [7229:1536]

1 duplicate frame(s)!
Pos:   4.8s    442f ( 7%)  0.00fps Trem:   0min  71mb  A-V:-0.021 [7256:1536]

1 duplicate frame(s)!
Pos:   4.9s    452f ( 7%)  0.00fps Trem:   0min  72mb  A-V:-0.021 [7281:1536]

1 duplicate frame(s)!
Pos:   5.0s    462f ( 7%)  0.00fps Trem:   0min  75mb  A-V:-0.021 [7307:1536]

1 duplicate frame(s)!
Pos:   5.2s    472f ( 7%)  0.00fps Trem:   0min  76mb  A-V:-0.021 [7318:1536]

1 duplicate frame(s)!
Pos:   5.3s    482f ( 7%)  0.00fps Trem:   0min  78mb  A-V:-0.021 [7380:1536]

1 duplicate frame(s)!
Pos:   5.4s    492f ( 7%)  0.00fps Trem:   0min  79mb  A-V:-0.021 [7424:1536]

1 duplicate frame(s)!
Pos:   5.5s    502f ( 7%)  0.00fps Trem:   0min  80mb  A-V:-0.021 [7477:1536]

1 duplicate frame(s)!
Pos:   5.6s    512f ( 7%)  0.00fps Trem:   0min  83mb  A-V:-0.021 [7509:1536]

1 duplicate frame(s)!
Pos:   5.7s    522f ( 7%)  0.00fps Trem:   0min  84mb  A-V:-0.021 [7528:1536]

1 duplicate frame(s)!
Pos:   5.8s    532f ( 7%)  0.00fps Trem:   0min  86mb  A-V:-0.021 [7571:1536]

1 duplicate frame(s)!
Pos:   5.9s    542f ( 7%)  0.00fps Trem:   0min  87mb  A-V:-0.021 [7580:1536]

1 duplicate frame(s)!
Pos:   6.0s    552f ( 7%)  0.00fps Trem:   0min  89mb  A-V:-0.021 [7607:1536]

1 duplicate frame(s)!
Pos:   6.2s    562f ( 7%)  0.00fps Trem:   0min  91mb  A-V:-0.021 [7656:1536]

1 duplicate frame(s)!
Pos:   6.3s    572f ( 7%)  0.00fps Trem:   0min  92mb  A-V:-0.021 [7694:1536]

1 duplicate frame(s)!
Pos:   6.4s    582f ( 7%)  0.00fps Trem:   0min  93mb  A-V:-0.021 [7737:1536]

1 duplicate frame(s)!
Pos:   6.5s    592f ( 7%)  0.00fps Trem:   0min  95mb  A-V:-0.021 [7765:1536]

1 duplicate frame(s)!
Pos:   6.6s    602f ( 7%)  0.00fps Trem:   0min  97mb  A-V:-0.021 [7802:1536]

1 duplicate frame(s)!
Pos:   6.7s    612f ( 7%)  0.00fps Trem:   0min  98mb  A-V:-0.021 [7820:1536]

1 duplicate frame(s)!
Pos:   6.8s    622f ( 7%)  0.00fps Trem:   0min 100mb  A-V:-0.021 [7853:1536]

1 duplicate frame(s)!
Pos:   6.9s    632f ( 7%)  0.00fps Trem:   0min 101mb  A-V:-0.021 [7878:1536]

1 duplicate frame(s)!
Pos:   7.0s    642f ( 7%)  0.00fps Trem:   0min 103mb  A-V:-0.021 [7912:1536]

1 duplicate frame(s)!
Pos:   7.1s    652f ( 7%)  0.00fps Trem:   0min 105mb  A-V:-0.021 [7947:1536]

1 duplicate frame(s)!
Pos:   7.2s    662f ( 7%)  0.00fps Trem:   0min 106mb  A-V:-0.021 [7991:1536]

1 duplicate frame(s)!
Pos:   7.4s    672f ( 7%)  0.00fps Trem:   0min 107mb  A-V:-0.021 [8012:1536]

1 duplicate frame(s)!
Pos:   7.5s    682f ( 7%)  0.00fps Trem:   0min 108mb  A-V:-0.021 [8050:1536]

1 duplicate frame(s)!
Pos:   7.6s    692f ( 7%)  0.00fps Trem:   0min 111mb  A-V:-0.021 [8075:1536]

1 duplicate frame(s)!
Pos:   7.7s    702f ( 7%)  0.00fps Trem:   0min 112mb  A-V:-0.021 [8108:1536]

1 duplicate frame(s)!
Pos:   7.8s    712f ( 8%)  0.00fps Trem:   0min 113mb  A-V:-0.021 [8130:1536]

1 duplicate frame(s)!
Pos:   7.9s    722f ( 8%)  0.00fps Trem:   0min 114mb  A-V:-0.021 [8141:1536]

1 duplicate frame(s)!
Pos:   8.0s    732f ( 8%)  0.00fps Trem:   0min 117mb  A-V:-0.021 [8163:1536]

1 duplicate frame(s)!
Pos:   8.1s    742f ( 8%)  0.00fps Trem:   0min 118mb  A-V:-0.021 [8178:1536]

1 duplicate frame(s)!
Pos:   8.2s    752f ( 8%)  0.00fps Trem:   0min 119mb  A-V:-0.021 [8196:1536]

1 duplicate frame(s)!
Pos:   8.3s    762f ( 8%)  0.00fps Trem:   0min 120mb  A-V:-0.021 [8200:1536]

1 duplicate frame(s)!
Pos:   8.5s    772f ( 8%)  0.00fps Trem:   0min 121mb  A-V:-0.021 [8218:1536]

1 duplicate frame(s)!
Pos:   8.6s    782f ( 8%)  0.00fps Trem:   0min 123mb  A-V:-0.021 [8224:1536]

1 duplicate frame(s)!
Pos:   8.7s    792f ( 8%)  0.00fps Trem:   0min 124mb  A-V:-0.021 [8243:1536]

1 duplicate frame(s)!
Pos:   8.8s    802f ( 8%)  0.00fps Trem:   0min 125mb  A-V:-0.021 [8257:1536]

1 duplicate frame(s)!
Pos:   8.9s    812f ( 8%)  0.00fps Trem:   0min 127mb  A-V:-0.021 [8299:1536]

1 duplicate frame(s)!
Pos:   9.0s    822f ( 8%)  0.00fps Trem:   0min 129mb  A-V:-0.021 [8319:1536]

1 duplicate frame(s)!
Pos:   9.1s    832f ( 8%)  0.00fps Trem:   0min 130mb  A-V:-0.021 [8324:1536]

1 duplicate frame(s)!
Pos:   9.2s    842f ( 8%)  0.00fps Trem:   0min 131mb  A-V:-0.021 [8339:1536]

1 duplicate frame(s)!
Pos:   9.3s    852f ( 8%)  0.00fps Trem:   0min 132mb  A-V:-0.021 [8355:1536]

1 duplicate frame(s)!
Pos:   9.4s    862f ( 8%)  0.00fps Trem:   0min 133mb  A-V:-0.021 [8368:1536]

1 duplicate frame(s)!
Pos:   9.6s    872f ( 8%)  0.00fps Trem:   0min 135mb  A-V:-0.021 [8380:1536]

1 duplicate frame(s)!
Pos:   9.7s    882f ( 8%)  0.00fps Trem:   0min 136mb  A-V:-0.021 [8392:1536]

1 duplicate frame(s)!
Pos:   9.8s    892f ( 8%)  0.00fps Trem:   0min 137mb  A-V:-0.021 [8397:1536]

1 duplicate frame(s)!
Pos:   9.9s    902f ( 8%)  0.00fps Trem:   0min 138mb  A-V:-0.021 [8410:1536]

1 duplicate frame(s)!
Pos:  10.0s    912f ( 8%)  0.00fps Trem:   0min 139mb  A-V:-0.021 [8414:1536]

1 duplicate frame(s)!
Pos:  10.1s    922f ( 8%)  0.00fps Trem:   0min 141mb  A-V:-0.021 [8422:1536]

1 duplicate frame(s)!
Pos:  10.2s    932f ( 8%)  0.00fps Trem:   0min 142mb  A-V:-0.021 [8426:1536]

1 duplicate frame(s)!
Pos:  10.3s    942f ( 8%)  0.00fps Trem:   0min 143mb  A-V:-0.021 [8439:1536]

1 duplicate frame(s)!
Pos:  10.4s    952f ( 8%)  0.00fps Trem:   0min 144mb  A-V:-0.021 [8448:1536]

1 duplicate frame(s)!
Pos:  10.6s    962f ( 8%)  0.00fps Trem:   0min 146mb  A-V:-0.021 [8458:1536]

1 duplicate frame(s)!
Pos:  10.7s    972f ( 8%)  0.00fps Trem:   0min 147mb  A-V:-0.021 [8472:1536]

1 duplicate frame(s)!
Pos:  10.8s    982f ( 8%)  0.00fps Trem:   0min 148mb  A-V:-0.021 [8491:1536]

1 duplicate frame(s)!
Pos:  10.9s    992f ( 8%)  0.00fps Trem:   0min 149mb  A-V:-0.021 [8519:1536]

1 duplicate frame(s)!
Pos:  11.0s   1002f ( 8%)  0.00fps Trem:   0min 150mb  A-V:-0.021 [8565:1536]

1 duplicate frame(s)!
Pos:  11.1s   1012f ( 8%)  0.00fps Trem:   0min 153mb  A-V:-0.021 [8631:1536]

1 duplicate frame(s)!
Pos:  11.2s   1022f ( 8%)  0.00fps Trem:   0min 154mb  A-V:-0.021 [8688:1536]

1 duplicate frame(s)!
Pos:  11.3s   1032f ( 8%)  0.00fps Trem:   0min 155mb  A-V:-0.021 [8725:1536]

1 duplicate frame(s)!
Pos:  11.4s   1042f ( 9%)  0.00fps Trem:   0min 156mb  A-V:-0.021 [8750:1536]

1 duplicate frame(s)!
Pos:  11.5s   1052f ( 9%)  0.00fps Trem:   0min 158mb  A-V:-0.021 [8759:1536]

1 duplicate frame(s)!
Pos:  11.7s   1062f ( 9%)  0.00fps Trem:   0min 160mb  A-V:-0.021 [8792:1536]

1 duplicate frame(s)!
Pos:  11.8s   1072f ( 9%)  0.00fps Trem:   0min 160mb  A-V:-0.021 [8804:1536]

1 duplicate frame(s)!
Pos:  11.9s   1082f ( 9%)  0.00fps Trem:   0min 161mb  A-V:-0.021 [8818:1536]

1 duplicate frame(s)!
Pos:  12.0s   1092f ( 9%)  0.00fps Trem:   0min 162mb  A-V:-0.021 [8820:1536]

1 duplicate frame(s)!
Pos:  12.1s   1102f ( 9%)  0.00fps Trem:   0min 164mb  A-V:-0.021 [8829:1536]

1 duplicate frame(s)!
Pos:  12.2s   1112f ( 9%)  0.00fps Trem:   0min 165mb  A-V:-0.021 [8834:1536]

1 duplicate frame(s)!
Pos:  12.3s   1122f ( 9%)  0.00fps Trem:   0min 166mb  A-V:-0.021 [8840:1536]

1 duplicate frame(s)!
Pos:  12.4s   1132f ( 9%)  0.00fps Trem:   0min 166mb  A-V:-0.021 [8841:1536]

1 duplicate frame(s)!
Pos:  12.5s   1142f ( 9%)  0.00fps Trem:   0min 168mb  A-V:-0.021 [8851:1536]

1 duplicate frame(s)!
Pos:  12.6s   1152f ( 9%)  0.00fps Trem:   0min 169mb  A-V:-0.021 [8851:1536]

1 duplicate frame(s)!
Pos:  12.8s   1162f ( 9%)  0.00fps Trem:   0min 170mb  A-V:-0.021 [8863:1536]

1 duplicate frame(s)!
Pos:  12.9s   1172f ( 9%)  0.00fps Trem:   0min 171mb  A-V:-0.021 [8864:1536]

1 duplicate frame(s)!
Pos:  13.0s   1182f ( 9%)  0.00fps Trem:   0min 171mb  A-V:-0.021 [8864:1536]

1 duplicate frame(s)!
Pos:  13.1s   1192f ( 9%)  0.00fps Trem:   0min 173mb  A-V:-0.021 [8862:1536]

1 duplicate frame(s)!
Pos:  13.2s   1202f ( 9%)  0.00fps Trem:   0min 174mb  A-V:-0.021 [8866:1536]

1 duplicate frame(s)!
Pos:  13.3s   1212f ( 9%)  0.00fps Trem:   0min 175mb  A-V:-0.021 [8865:1536]

1 duplicate frame(s)!
Pos:  13.4s   1222f ( 9%)  0.00fps Trem:   0min 175mb  A-V:-0.021 [8870:1536]

1 duplicate frame(s)!
Pos:  13.5s   1232f ( 9%)  0.00fps Trem:   0min 177mb  A-V:-0.021 [8895:1536]

1 duplicate frame(s)!
Pos:  13.6s   1242f ( 9%)  0.00fps Trem:   0min 178mb  A-V:-0.021 [8907:1536]

1 duplicate frame(s)!
Pos:  13.7s   1252f ( 9%)  0.00fps Trem:   0min 179mb  A-V:-0.021 [8910:1536]

1 duplicate frame(s)!
Pos:  13.8s   1262f ( 9%)  0.00fps Trem:   0min 180mb  A-V:-0.021 [8911:1536]

1 duplicate frame(s)!
Pos:  14.0s   1272f ( 9%)  0.00fps Trem:   0min 181mb  A-V:-0.021 [8922:1536]

1 duplicate frame(s)!
Pos:  14.1s   1282f ( 9%)  0.00fps Trem:   0min 182mb  A-V:-0.021 [8927:1536]

1 duplicate frame(s)!
Pos:  14.2s   1292f ( 9%)  0.00fps Trem:   0min 183mb  A-V:-0.021 [8937:1536]

1 duplicate frame(s)!
Pos:  14.3s   1302f ( 9%)  0.00fps Trem:   0min 184mb  A-V:-0.021 [8944:1536]

1 duplicate frame(s)!
Pos:  14.4s   1312f ( 9%)  0.00fps Trem:   0min 185mb  A-V:-0.021 [8981:1536]

1 duplicate frame(s)!
Pos:  14.5s   1322f ( 9%)  0.00fps Trem:   0min 186mb  A-V:-0.021 [8989:1536]

1 duplicate frame(s)!
Pos:  14.6s   1332f ( 9%)  0.00fps Trem:   0min 186mb  A-V:-0.021 [8999:1536]

1 duplicate frame(s)!
Pos:  14.7s   1342f ( 9%)  0.00fps Trem:   0min 187mb  A-V:-0.021 [9001:1536]

1 duplicate frame(s)!
Pos:  14.8s   1352f ( 9%)  0.00fps Trem:   0min 188mb  A-V:-0.021 [9006:1536]

1 duplicate frame(s)!
Pos:  14.9s   1362f ( 9%)  0.00fps Trem:   0min 189mb  A-V:-0.021 [9005:1536]

1 duplicate frame(s)!
Pos:  15.0s   1366f ( 9%)  0.00fps Trem:   0min 189mb  A-V:-0.015 [9003:1536]
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream: 8997.948 kbit/s  (1124743 B/s)  size: 16882401 bytes  15.010 secs  1366 frames

Audio stream: 1536.000 kbit/s  (192000 B/s)  size: 2880000 bytes  15.000 secs
```

---

### Post by Andrew Golightly on 2012-06-10
> **FakeOutdoorsman said:**
> Can you show your actual ffmpeg command and the complete console output?
Are you using 12.04 as your profile states?
What player are you using?
Does the output play normally with ffplay?

Note that options placed before *-i* are intended to be applied to the input; therefore *-vcodec copy -acodec copy* should be placed past *-i input* so it is applied to the output. The version you are using probably is applying these options to the output as you are intending, but this won't work with a newer ffmpeg resulting in *Unknown decoder 'copy'*.

Whoops, sorry.. you asked about ffmpeg.


> andrew@Merlin:~/Desktop$ ffmpeg -vcodec copy -acodec copy -i Sohum\ Sai.m4v -ss 00:02:46 -t 00:00:15 theMind.m4v
ffmpeg version 0.8.1-4:0.8.1-0ubuntu1, Copyright (c) 2000-2011 the Libav developers
  built on Mar 22 2012 05:09:06 with gcc 4.6.3
This program is not developed anymore and is only provided for compatibility. Use avconv instead (see Changelog for the list of incompatible changes).

Seems stream 0 codec frame rate differs from container frame rate: 180000.00 (180000/1) -> 100.00 (100/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Sohum Sai.m4v':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: mp42isomavc1
    creation_time   : 2012-06-08 03:44:28
    encoder         : HandBrake 4714svn 2012060701
  Duration: 00:36:54.14, start: 0.000000, bitrate: 1863 kb/s
    Stream #0.0(und): Video: h264 (High), yuv420p, 720x576 [PAR 1536:1435 DAR 384:287], 1537 kb/s, 24.68 fps, 100 tbr, 90k tbn, 180k tbc
    Metadata:
      creation_time   : 2012-06-08 03:44:28
    Stream #0.1(und): Audio: aac, 48000 Hz, stereo, s16, 159 kb/s
    Metadata:
      creation_time   : 2012-06-08 03:44:28
    Stream #0.2(und): Audio: ac3, 48000 Hz, stereo, s16, 160 kb/s
    Metadata:
      creation_time   : 2012-06-08 03:44:28
Output #0, ipod, to 'theMind.m4v':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: mp42isomavc1
    creation_time   : 2012-06-08 03:44:28
    encoder         : Lavf53.21.0
    Stream #0.0(und): Video: avc1 / 0x31637661, yuv420p, 720x576 [PAR 1536:1435 DAR 384:287], q=2-31, 1537 kb/s, 90k tbn, 90k tbc
    Metadata:
      creation_time   : 2012-06-08 03:44:28
    Stream #0.1(und): Audio: aac, 48000 Hz, stereo, 159 kb/s
    Metadata:
      creation_time   : 2012-06-08 03:44:28
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press ctrl-c to stop encoding
frame=  297 fps=  0 q=-1.0 Lsize=    2902kB time=14.88 bitrate=1597.9kbits/s    
video:2598kB audio:293kB global headers:0kB muxing overhead 0.401469%


What happens when I play it in ffplay/VLC is the first few seconds of video are in slow-motion, and then suddenly it syncs and is okay. So probably the closest to working to date.

I also tried to put the "-i" as you said before the other options:

> ffmpeg -i Sohum\ Sai.m4v -vcodec copy -acodec copy -ss 00:02:46 -t 00:00:15 theMind.m4v

and no difference to output

---

### Post by FakeOutdoorsman on 2012-06-10
I'm not really sure what the issue is. Usually in this case I suggest trying the most recent ffmpeg. It's easy to try since you don't even have to install it, but you'll need a few build dependencies, and this won't interfere with your currently installed ffmpeg.

```
sudo apt-get install build-essential yasm
cd
wget -O ffmpeg.tar.gz "http://git.videolan.org/?p=ffmpeg.git;a=snapshot;h=HEAD;sf=tgz"
tar xzvf ffmpeg.tar.gz
cd ffmpeg-HEAD-*
./configure
make -j2
```

Now try your command:
```
cd ~/ffmpeg-HEAD-*
./ffmpeg -i ~/Sohum\ Sai.m4v -vcodec copy -acodec copy -ss 00:02:46 -t 00:00:15 ~/theMind.m4v
```

If it plays normally then we know the issue occurred somewhere with the trimming or muxing step of the command of the old ffmpeg. If it still occurs that should indicate that recent ffmpeg does not contain a fix for the issue and/or that perhaps there is an issue with decoding and not trimming or muxing.

I forgot to ask: does the input file play back normally? Would it be possible for you to upload a sample of the output that has the playback issue?

---

### Post by Andrew Golightly on 2012-06-10
> **FakeOutdoorsman said:**
> I'm not really sure what the issue is. Usually in this case I suggest trying the most recent ffmpeg. It's easy to try since you don't even have to install it, but you'll need a few build dependencies, and this won't interfere with your currently installed ffmpeg.

```
sudo apt-get install build-essential yasm
cd
wget -O ffmpeg.tar.gz "http://git.videolan.org/?p=ffmpeg.git;a=snapshot;h=HEAD;sf=tgz"
tar xzvf ffmpeg.tar.gz
cd ffmpeg-HEAD-*
./configure
make -j2
```

Now try your command:
```
cd ~/ffmpeg-HEAD-*
./ffmpeg -i ~/Sohum\ Sai.m4v -vcodec copy -acodec copy -ss 00:02:46 -t 00:00:15 ~/theMind.m4v
```

If it plays normally then we know the issue occurred somewhere with the trimming or muxing step of the command of the old ffmpeg. If it still occurs that should indicate that recent ffmpeg does not contain a fix for the issue and/or that perhaps there is an issue with decoding and not trimming or muxing.

I forgot to ask: does the input file play back normally? Would it be possible for you to upload a sample of the output that has the playback issue?

I tried another two random samples...

> ffmpeg -i Sohum\ Sai.m4v -vcodec copy -acodec copy -ss 00:11:11 -t 00:01:11 clip2.m4v

and

> ffmpeg -i Sohum\ Sai.m4v -vcodec copy -acodec copy -ss 00:00:00 -t 00:01:11 clip.m4v

and they played back fine. So not really sure what's going on either now. Thanks for talking me through it.

---

### Post by mc4man on 2012-06-10
I don't think that on 12.04 using the command 'ffmpeg <whatever>' is any assurance that the ffmpeg binary that the Libav boys half-heartedly supplied is going to produce good results. Even the version # could be suspect.

So I'd either go ahead & use 'avconv <whatever>' or remove the supplied ffmpeg binary & build your own, full instructions linked below
(or just continue to use the locally built as FO has shown

[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)
author's previous referring thread - 
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

This should remove the Libav supplied ffmpeg binary if going that route
```
sudo apt-get purge libav-tools
```

---

### Post by FakeOutdoorsman on 2012-06-10
> **mc4man said:**
> This should remove the Libav supplied ffmpeg binary if going that route
```
sudo apt-get purge libav-tools
```

I forgot to add that to the 12.04 guide... Tells you how much I have I've been paying attention to that package.

---

### Post by mc4man on 2012-06-10
> **FakeOutdoorsman said:**
> I forgot to add that to the 12.04 guide... Tells you how much I have I've been paying attention to that package.

I would suspect that come 12.10 there won't be any ffmpeg binary in the libav* source or maybe 13.04

There is certainly an interesting split as to who 'uses' what, just noticed that gstreamer is going with libav in the 1.0 (0.11) series for it's gst plugin

For most gstreamer is just providing decoding, so in that regard Ubuntu/Debian users will, if anything,  be slightly behind the curve.  (it seems FFmpeg is a bit more active in new or improved decoding, libav picks up on as & when  they see fit.

---

### Post by shantiq on 2012-06-11
> **Andrew Golightly said:**
> Thanks Shantiq. Yes, I needed to add pcm for the command to execute. The output doesn't work though.. audio plays at correct pace, and the video looks like someone has it on intermittent fast forward bursts. So I take it I need to encode it as something different to start with now? Or edit the mencoder line to encode with something else?


well i am surprised here:KS  

>  looks like someone has it on intermittent fast forward bursts.


sounds like there is something odd about the input file

how was it made?   is it a rip?   from a camera?

could you show us a mediainfo  

```
sudo apt-get install mediainfo

```


then  ```
mediainfo    file.extension
```    and share it here   if you do not mind

or **and** also as you say **reencode original file  with handbrake to mkv with MPEG-4 ffmpeg**[ATTACH]219513[/ATTACH]

i found this to be really stable for files you want to manipulate


and then do same cutting again with mencoder and /or ffmpeg




**============================**


oh   and then   saw it was solved     well good then   :::]]

---

