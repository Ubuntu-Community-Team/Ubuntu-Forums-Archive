---
title: "Trouble clipping from a video"
date: 2012-07-07
forum: Multimedia Software
---

### Post by Stonecold1995 on 2012-07-07
I have a .mkv file from a TV show and I want to save the video content between 20:40 and 22:25 as a separate file (basically clip it out without modifying the original).  The .mkv file is very high quality (each 25 minute episode is about 1.3 GB in size).  Anyways, I tried using VLC's record function, but it butchered the quality.  I also tried using FFmpeg to cut it, but it was unable to do it (it gave some error about a framebuffer not being full.  I also tried using Transmageddon, but it was unable to process the video either.

Here's the video's codec information, if it makes any difference.
[IMG]http://i47.tinypic.com/f0osxc.png[/IMG]

So what tools should I use to do this?

---

### Post by shantiq on 2012-07-08
maybe try this

> mencoder  -ss 00:20:40  -endpos 00:01:45 -oac copy -ovc copy original.mkv -o newfile.mkv



if 1:45 is the length of cut that you want

---

### Post by Merrattic on 2012-07-08
And what was the ffmpeg command you used? Also ffmpeg from repos or compiled? Does same command work OK on other videos (not necessarily from the same set!)? Are you getting any audio conversion errors ?

---

### Post by Stonecold1995 on 2012-07-08
> **Merrattic said:**
> And what was the ffmpeg command you used? Also ffmpeg from repos or compiled? Does same command work OK on other videos (not necessarily from the same set!)? Are you getting any audio conversion errors ?

This is the message I get with the command I used:
```
alex@kubuntu:~/Videos/Mahou Shoujo Madoka Magica$ ffmpeg -i 'Episode 7.mkv' -ss 00:20:47 -t 00:22:26 clip.mkv
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[matroska,webm @ 0x23349c0] max_analyze_duration reached
[matroska,webm @ 0x23349c0] Estimating duration from bitrate, this may be inaccurate
Input #0, matroska,webm, from 'Episode 7.mkv':
  Metadata:
    title           : Mahou Shoujo Madoka Magika Episode 07 - Can You Face Your True Feelings
  Duration: 00:24:12.09, start: 0.000000, bitrate: N/A
    Chapter #0.0: start 0.000000, end 158.116000
    Metadata:
      title           : Prologue
    Chapter #0.1: start 158.116000, end 248.081000
    Metadata:
      title           : Opening
    Chapter #0.2: start 248.081000, end 727.018000
    Metadata:
      title           : Part A
    Chapter #0.3: start 727.018000, end 1346.011000
    Metadata:
      title           : Part B
    Chapter #0.4: start 1346.011000, end 1436.060000
    Metadata:
      title           : Ending
    Chapter #0.5: start 1436.060000, end 1452.095000
    Metadata:
      title           : Preview
    Stream #0.0(jpn): Video: h264 (High 10), yuv420p10le, 1920x1080 [PAR 1:1 DAR 16:9], 23.98 fps, 23.98 tbr, 1k tbn, 47.95 tbc (default)
    Metadata:
      title           : Video track
    Stream #0.1(jpn): Audio: flac, 48000 Hz, 2 channels, s32 (default)
    Metadata:
      title           : Audio track
    Stream #0.2(jpn): Audio: aac, 48000 Hz, stereo, s16
    Metadata:
      title           : Audio track - Commentary
    Stream #0.3(eng): Subtitle: *** (default)
    Metadata:
      title           : Subtitle track
    Stream #0.4(eng): Subtitle: ***
    Metadata:
      title           : Subtitle track - Commentary
    Stream #0.5(eng): Subtitle: ***
    Metadata:
      title           : Subtitle track - Colorless
    Stream #0.6: Attachment: [0][0][0][0] / 0x0000
    Metadata:
      filename        : Doradani_Rg_Bold.ttf
      mimetype        : application/x-truetype-font
    Stream #0.7: Attachment: [0][0][0][0] / 0x0000
    Metadata:
      filename        : Doradani Rg Bold Italic.ttf
      mimetype        : application/x-truetype-font
    Stream #0.8: Attachment: [0][0][0][0] / 0x0000
    Metadata:
      filename        : FOT-GrecoStd-M-ED3-8v2.otf
      mimetype        : application/x-truetype-font
    Stream #0.9: Attachment: [0][0][0][0] / 0x0000
    Metadata:
      filename        : PRISTINA-ED3-8v2.TTF
      mimetype        : application/x-truetype-font
    Stream #0.10: Attachment: [0][0][0][0] / 0x0000
    Metadata:
      filename        : love-OPv3.ttf
      mimetype        : application/x-truetype-font
    Stream #0.11: Attachment: [0][0][0][0] / 0x0000
    Metadata:
      filename        : angelina.ttf
      mimetype        : application/x-truetype-font
    Stream #0.12: Attachment: [0][0][0][0] / 0x0000
    Metadata:
      filename        : ARIALUNI-ep07.TTF
      mimetype        : application/x-truetype-font
    Stream #0.13: Attachment: [0][0][0][0] / 0x0000
    Metadata:
      filename        : mona-ep07.ttf
      mimetype        : application/x-truetype-font
    Stream #0.14: Attachment: [0][0][0][0] / 0x0000
    Metadata:
      filename        : tahoma-ep07.ttf
      mimetype        : application/x-truetype-font
Incompatible pixel format 'yuv420p10le' for codec 'mpeg4', auto-selecting format 'yuv420p'
[buffer @ 0x26a3ae0] w:1920 h:1080 pixfmt:yuv420p10le
[avsink @ 0x24c8ac0] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0x2736500] w:1920 h:1080 fmt:yuv420p10le -> w:1920 h:1080 fmt:yuv420p flags:0x4
Output #0, matroska, to 'clip.mkv':
  Metadata:
    title           : Mahou Shoujo Madoka Magika Episode 07 - Can You Face Your True Feelings
    encoder         : Lavf53.21.0
    Chapter #0.0: start 0.000000, end 99.011000
    Metadata:
      title           : Part B
    Chapter #0.1: start 99.011000, end 189.060000
    Metadata:
      title           : Ending
    Chapter #0.2: start 189.060000, end 205.095000
    Metadata:
      title           : Preview
    Stream #0.0(jpn): Video: mpeg4, yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], q=2-31, 200 kb/s, 1k tbn, 23.98 tbc (default)
    Metadata:
      title           : Video track
    Stream #0.1(jpn): Audio: libvorbis, 48000 Hz, stereo, s16, 200 kb/s
    Metadata:
      title           : Audio track - Commentary
    Stream #0.2(eng): Subtitle: ***, 200 kb/s
    Metadata:
      title           : Subtitle track - Commentary
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.2 -> #0.1
  Stream #0.4 -> #0.2
Press ctrl-c to stop encoding
[buffer @ 0x26a3ae0] Buffering several frames is not supported. Please consume all available frames before adding a new one.
^C    Last message repeated 10276 times  6kB time=10000000000.00 bitrate=   0.0kbits/s    
Buffering several frames is not supported. Please consume all available frames before adding a new one.
[buffer @ 0x26a3ae0] Buffering several frames is not supported. Please consume all available frames before adding a new one.
    Last message repeated 1 times
frame=    0 fps=  0 q=0.0 Lsize=       6kB time=10000000000.00 bitrate=   0.0kbits/s    
video:0kB audio:0kB global headers:5kB muxing overhead 23.880597%
Received signal 2: terminating.
```

I tried using it on a different .mkv file from a different show (also with a smaller file size) and got this:
```
alex@kubuntu:~/Videos/Chobits$ ffmpeg -i 'Episode 7.mkv' -ss 00:20:47 -t 00:22:26 clip.mkv                                                                                                                                                                                     
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers                                                                                                                                                                                    
  built on Jun 12 2012 16:52:09 with gcc 4.6.3                                                                                                                                                                                                                                 
*** THIS PROGRAM IS DEPRECATED ***                                                                                                                                                                                                                                             
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.                                                                                                                                                            
[matroska,webm @ 0x1ecb9c0] max_analyze_duration reached                                                                                                                                                                                                                       
[matroska,webm @ 0x1ecb9c0] Estimating duration from bitrate, this may be inaccurate
Input #0, matroska,webm, from 'Episode 7.mkv':
  Duration: 00:24:38.64, start: 0.000000, bitrate: N/A
    Stream #0.0(eng): Subtitle: [0][0][0][0] / 0x0000 (default)
    Metadata:
      title           : No Subtitles
    Stream #0.1(eng): Audio: aac, 48000 Hz, stereo, s16 (default)
    Metadata:
      title           : English
    Stream #0.2(jpn): Audio: aac, 48000 Hz, stereo, s16
    Metadata:
      title           : Japanese
    Stream #0.3(jpn): Subtitle: [0][0][0][0] / 0x0000
    Metadata:
      title           : English
    Stream #0.4: Video: h264 (High), yuv420p, 640x352, PAR 1:1 DAR 20:11, 23.98 fps, 23.98 tbr, 1k tbn, 47.95 tbc (default)
[buffer @ 0x1eff060] w:640 h:352 pixfmt:yuv420p
Output #0, matroska, to 'clip.mkv':
    Stream #0.0: Video: mpeg4, yuv420p, 640x352 [PAR 1:1 DAR 20:11], q=2-31, 200 kb/s, 90k tbn, 23.98 tbc (default)
    Stream #0.1(eng): Audio: libvorbis, 48000 Hz, stereo, s16, 200 kb/s (default)
    Metadata:
      title           : English
    Stream #0.2(eng): Subtitle: ***, 200 kb/s (default)
    Metadata:
      title           : No Subtitles
Stream mapping:
  Stream #0.4 -> #0.0
  Stream #0.1 -> #0.1
  Stream #0.0 -> #0.2
Decoder (codec id 94210) not found for input stream #0.0
```

It says to use avconv, but I don't know how to use it and there are way too many options to go through.

---

### Post by Stonecold1995 on 2012-07-08
> **shantiq said:**
> maybe try this


> mencoder -ss 00:20:40 -endpos 00:01:45 -oac copy -ovc copy original.mkv -o newfile.mkv


if 1:45 is the length of cut that you want

I just tried that.  It almost worked.  It started at the right point, but didn't stop where I told it to and continued on through the remainder of the video.  Also, it did not save the subtitles (which I forgot to mention I need copied as well) and the playback seemed a bit slow (not like it was a slow video, but like it was taxing on the CPU because it began to lag at some parts).

Here's the complete output of that command:
```
alex@kubuntu:~/Videos/Mahou Shoujo Madoka Magica$ mencoder -ss 00:20:40 -endpos 00:22:25 -oac copy -ovc copy 'Episode 7.mkv' -o output.mkv
MEncoder svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team                                                                                                                                                                                                    
                                                                                                                                                                                                                                                                               
WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.                                                                                                                                                                                                                            
success: format: 0  data: 0x0 - 0x50d266ff                                                                                                                                                                                                                                     
libavformat version 53.21.0 (external)                                                                                                                                                                                                                                         
Mismatching header version 53.19.0                                                                                                                                                                                                                                             
libavformat file format detected.                                                                                                                                                                                                                                              
[matroska,webm @ 0x7f2d124b6940]max_analyze_duration reached                                                                                                                                                                                                                   
[matroska,webm @ 0x7f2d124b6940]Estimating duration from bitrate, this may be inaccurate                                                                                                                                                                                       
[lavf] stream 0: video (h264), -vid 0, Video track                                                                                                                                                                                                                             
[lavf] stream 1: audio (flac), -aid 0, -alang jpn, Audio track                                                                                                                                                                                                                 
[lavf] stream 2: audio (aac), -aid 1, -alang jpn, Audio track - Commentary                                                                                                                                                                                                     
[lavf] stream 3: subtitle (***), -sid 0, -slang eng, Subtitle track                                                                                                                                                                                                            
[lavf] stream 4: subtitle (***), -sid 1, -slang eng, Subtitle track - Commentary                                                                                                                                                                                               
[lavf] stream 5: subtitle (***), -sid 2, -slang eng, Subtitle track - Colorless                                                                                                                                                                                                
VIDEO:  [H264]  1920x1080  0bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)                                                                                                                                                                                                         
[V] filefmt:44  fourcc:0x34363248  size:1920x1080  fps:23.976  ftime:=0.0417                                                                                                                                                                                                   
==========================================================================                                                                                                                                                                                                     
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders                                                                                                                                                                                                               
libavcodec version 53.35.0 (external)                                                                                                                                                                                                                                          
Mismatching header version 53.32.2                                                                                                                                                                                                                                             
AUDIO: 48000 Hz, 2 ch, s32le, 0.0 kbit/0.00% (ratio: 0->384000)                                                                                                                                                                                                                
Selected audio codec: [ffflac] afm: ffmpeg (FFmpeg FLAC audio)                                                                                                                                                                                                                 
==========================================================================                                                                                                                                                                                                     
videocodec: framecopy (1920x1080 0bpp fourcc=34363248)                                                                                                                                                                                                                         
audiocodec: framecopy (format=f1ac chans=2 rate=48000 bits=0 B/s=0 sample-0)                                                                                                                                                                                                   
Writing header...                                                                                                                                                                                                                                                              
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.8s     21f (65%)  0.00fps Trem:   0min   1mb  A-V:-0.083 [0:1767]

1 duplicate frame(s)!
Pos:   1.3s     31f (65%)  0.00fps Trem:   0min   2mb  A-V:-0.083 [8794:1756]

1 duplicate frame(s)!
Pos:   1.8s     41f (65%)  0.00fps Trem:   0min   3mb  A-V:-0.083 [7777:1749]

1 duplicate frame(s)!
Pos:   2.2s     51f (65%)  0.00fps Trem:   0min   3mb  A-V:-0.083 [7239:1737]

1 duplicate frame(s)!
Pos:   2.7s     61f (65%)  0.00fps Trem:   0min   4mb  A-V:-0.083 [6415:1728]

1 duplicate frame(s)!
Pos:   3.1s     71f (65%)  0.00fps Trem:   0min   4mb  A-V:-0.083 [5817:1721]

1 duplicate frame(s)!
Pos:   3.6s     81f (65%)  0.00fps Trem:   0min   4mb  A-V:-0.083 [5280:1703]

1 duplicate frame(s)!
Pos:   4.0s     91f (65%)  0.00fps Trem:   0min   5mb  A-V:-0.083 [5868:1683]

1 duplicate frame(s)!
Pos:   4.5s    101f (65%)  0.00fps Trem:   0min   6mb  A-V:-0.083 [6188:1678]

1 duplicate frame(s)!
Pos:   5.0s    111f (65%)  0.00fps Trem:   0min   7mb  A-V:-0.083 [6671:1691]

1 duplicate frame(s)!
Pos:   5.4s    121f (65%)  0.00fps Trem:   0min   8mb  A-V:-0.083 [6880:1702]

1 duplicate frame(s)!
Pos:   5.9s    131f (65%)  0.00fps Trem:   0min   9mb  A-V:-0.083 [7169:1708]

1 duplicate frame(s)!
Pos:   6.3s    141f (65%)  0.00fps Trem:   0min  10mb  A-V:-0.083 [7219:1715]

1 duplicate frame(s)!
Pos:   6.8s    151f (65%)  0.00fps Trem:   0min  11mb  A-V:-0.083 [7369:1719]

1 duplicate frame(s)!
Pos:   7.3s    161f (65%)  0.00fps Trem:   0min  12mb  A-V:-0.083 [7278:1724]

1 duplicate frame(s)!
Pos:   7.7s    171f (65%)  0.00fps Trem:   0min  12mb  A-V:-0.083 [7392:1728]

1 duplicate frame(s)!
Pos:   8.2s    181f (65%)  0.00fps Trem:   0min  13mb  A-V:-0.083 [7408:1732]

1 duplicate frame(s)!
Pos:   8.6s    191f (65%)  0.00fps Trem:   0min  14mb  A-V:-0.083 [7552:1735]

1 duplicate frame(s)!
Pos:   9.1s    201f (65%)  0.00fps Trem:   0min  15mb  A-V:-0.083 [7708:1737]

1 duplicate frame(s)!
Pos:   9.6s    211f (65%)  0.00fps Trem:   0min  16mb  A-V:-0.083 [7749:1738]

1 duplicate frame(s)!
Pos:  10.0s    221f (65%)  0.00fps Trem:   0min  17mb  A-V:-0.083 [8001:1738]

1 duplicate frame(s)!
Pos:  10.5s    231f (66%)  0.00fps Trem:   0min  18mb  A-V:-0.083 [8190:1742]

1 duplicate frame(s)!
Pos:  10.9s    241f (66%)  0.00fps Trem:   0min  19mb  A-V:-0.083 [8300:1743]

1 duplicate frame(s)!
Pos:  11.4s    251f (66%)  0.00fps Trem:   0min  20mb  A-V:-0.083 [8144:1745]

1 duplicate frame(s)!
Pos:  11.8s    261f (66%)  0.00fps Trem:   0min  20mb  A-V:-0.083 [7890:1748]

1 duplicate frame(s)!
Pos:  12.3s    271f (66%)  0.00fps Trem:   0min  21mb  A-V:-0.083 [7637:1754]

1 duplicate frame(s)!
Pos:  12.8s    281f (66%)  0.00fps Trem:   0min  21mb  A-V:-0.083 [7534:1757]

1 duplicate frame(s)!
Pos:  13.2s    291f (66%)  0.00fps Trem:   0min  22mb  A-V:-0.083 [7523:1761]

1 duplicate frame(s)!
Pos:  13.7s    301f (66%)  0.00fps Trem:   0min  23mb  A-V:-0.083 [7553:1763]

1 duplicate frame(s)!
Pos:  14.1s    311f (66%)  0.00fps Trem:   0min  24mb  A-V:-0.083 [7625:1766]

1 duplicate frame(s)!
Pos:  14.6s    321f (66%)  0.00fps Trem:   0min  24mb  A-V:-0.083 [7626:1767]

1 duplicate frame(s)!
Pos:  15.1s    331f (66%)  0.00fps Trem:   0min  25mb  A-V:-0.083 [7619:1765]

1 duplicate frame(s)!
Pos:  15.5s    341f (66%)  0.00fps Trem:   0min  26mb  A-V:-0.083 [7622:1762]

1 duplicate frame(s)!
Pos:  16.0s    351f (66%)  0.00fps Trem:   0min  27mb  A-V:-0.083 [7599:1763]

1 duplicate frame(s)!
Pos:  16.4s    361f (66%)  0.00fps Trem:   0min  27mb  A-V:-0.083 [7628:1765]

1 duplicate frame(s)!
Pos:  16.9s    371f (66%)  0.00fps Trem:   0min  28mb  A-V:-0.083 [7642:1767]

1 duplicate frame(s)!
Pos:  17.4s    381f (66%)  0.00fps Trem:   0min  29mb  A-V:-0.083 [7669:1768]

1 duplicate frame(s)!
Pos:  17.8s    391f (66%)  0.00fps Trem:   0min  30mb  A-V:-0.083 [7712:1769]

1 duplicate frame(s)!
Pos:  18.3s    401f (66%)  0.00fps Trem:   0min  31mb  A-V:-0.083 [7761:1771]

1 duplicate frame(s)!
Pos:  18.7s    411f (66%)  0.00fps Trem:   0min  32mb  A-V:-0.083 [7783:1773]

1 duplicate frame(s)!
Pos:  19.2s    421f (66%)  0.00fps Trem:   0min  33mb  A-V:-0.083 [7819:1777]

1 duplicate frame(s)!
Pos:  19.6s    431f (66%)  0.00fps Trem:   0min  33mb  A-V:-0.083 [7825:1779]

1 duplicate frame(s)!
Pos:  20.1s    441f (66%)  0.00fps Trem:   0min  34mb  A-V:-0.083 [7799:1778]

1 duplicate frame(s)!
Pos:  20.6s    451f (66%)  0.00fps Trem:   0min  35mb  A-V:-0.083 [7793:1778]

1 duplicate frame(s)!
Pos:  21.0s    461f (66%)  0.00fps Trem:   0min  36mb  A-V:-0.083 [7794:1779]

1 duplicate frame(s)!
Pos:  21.5s    471f (67%)  0.00fps Trem:   0min  36mb  A-V:-0.083 [7786:1779]

1 duplicate frame(s)!
Pos:  21.9s    481f (67%)  0.00fps Trem:   0min  37mb  A-V:-0.083 [7859:1778]

1 duplicate frame(s)!
Pos:  22.4s    491f (67%)  0.00fps Trem:   0min  38mb  A-V:-0.083 [7975:1775]

1 duplicate frame(s)!
Pos:  22.9s    501f (67%)  0.00fps Trem:   0min  39mb  A-V:-0.083 [7961:1773]

1 duplicate frame(s)!
Pos:  23.3s    511f (67%)  0.00fps Trem:   0min  40mb  A-V:-0.083 [7914:1776]

1 duplicate frame(s)!
Pos:  23.8s    521f (67%)  0.00fps Trem:   0min  40mb  A-V:-0.083 [7910:1777]

1 duplicate frame(s)!
Pos:  24.2s    531f (67%)  0.00fps Trem:   0min  41mb  A-V:-0.083 [7937:1778]

1 duplicate frame(s)!
Pos:  24.7s    541f (67%)  0.00fps Trem:   0min  42mb  A-V:-0.083 [7972:1779]

1 duplicate frame(s)!
Pos:  25.2s    551f (67%)  0.00fps Trem:   0min  43mb  A-V:-0.083 [8003:1779]

1 duplicate frame(s)!
Pos:  25.6s    561f (67%)  0.00fps Trem:   0min  44mb  A-V:-0.083 [8032:1780]

1 duplicate frame(s)!
Pos:  26.1s    571f (67%)  0.00fps Trem:   0min  45mb  A-V:-0.083 [8082:1782]

1 duplicate frame(s)!
Pos:  26.5s    581f (67%)  0.00fps Trem:   0min  46mb  A-V:-0.083 [8132:1782]

1 duplicate frame(s)!
Pos:  27.0s    591f (67%)  0.00fps Trem:   0min  47mb  A-V:-0.083 [8152:1784]

1 duplicate frame(s)!
Pos:  27.4s    601f (67%)  0.00fps Trem:   0min  48mb  A-V:-0.083 [8157:1787]

1 duplicate frame(s)!
Pos:  27.9s    611f (67%) 400.39fps Trem:   0min  48mb  A-V:-0.083 [8111:1791]

1 duplicate frame(s)!
Pos:  28.4s    621f (67%) 406.68fps Trem:   0min  49mb  A-V:-0.083 [8067:1793]

1 duplicate frame(s)!
Pos:  28.8s    631f (67%) 406.83fps Trem:   0min  50mb  A-V:-0.083 [8136:1795]

1 duplicate frame(s)!
Pos:  29.3s    641f (67%) 413.02fps Trem:   0min  51mb  A-V:-0.083 [8146:1797]

1 duplicate frame(s)!
Pos:  29.7s    651f (67%) 417.84fps Trem:   0min  52mb  A-V:-0.083 [8160:1798]

1 duplicate frame(s)!
Pos:  30.2s    661f (68%) 417.56fps Trem:   0min  52mb  A-V:-0.083 [8155:1799]

1 duplicate frame(s)!
Pos:  30.7s    671f (68%) 401.56fps Trem:   0min  53mb  A-V:-0.083 [8144:1798]

1 duplicate frame(s)!
Pos:  31.1s    681f (68%) 407.30fps Trem:   0min  54mb  A-V:-0.083 [8151:1798]

1 duplicate frame(s)!
Pos:  31.6s    691f (68%) 413.03fps Trem:   0min  55mb  A-V:-0.083 [8159:1797]

1 duplicate frame(s)!
Pos:  32.0s    701f (68%) 418.51fps Trem:   0min  56mb  A-V:-0.083 [8179:1796]

1 duplicate frame(s)!
Pos:  32.5s    711f (68%) 424.22fps Trem:   0min  57mb  A-V:-0.083 [8215:1796]

1 duplicate frame(s)!
Pos:  32.9s    721f (68%) 429.93fps Trem:   0min  58mb  A-V:-0.083 [8248:1795]

1 duplicate frame(s)!
Pos:  33.4s    731f (68%) 434.86fps Trem:   0min  59mb  A-V:-0.083 [8318:1794]

1 duplicate frame(s)!
Pos:  33.9s    741f (68%) 435.11fps Trem:   0min  60mb  A-V:-0.083 [8337:1793]

1 duplicate frame(s)!
Pos:  34.3s    751f (68%) 440.73fps Trem:   0min  60mb  A-V:-0.083 [8291:1793]

1 duplicate frame(s)!
Pos:  34.8s    761f (68%) 446.33fps Trem:   0min  61mb  A-V:-0.083 [8273:1793]

1 duplicate frame(s)!
Pos:  35.2s    771f (68%) 445.15fps Trem:   0min  61mb  A-V:-0.083 [8239:1793]

1 duplicate frame(s)!
Pos:  35.7s    781f (68%) 450.92fps Trem:   0min  62mb  A-V:-0.083 [8149:1794]

1 duplicate frame(s)!
Pos:  36.2s    791f (68%) 456.43fps Trem:   0min  62mb  A-V:-0.083 [8053:1795]

1 duplicate frame(s)!
Pos:  36.6s    801f (68%) 461.94fps Trem:   0min  62mb  A-V:-0.083 [7961:1796]

1 duplicate frame(s)!
Pos:  37.1s    811f (68%) 461.32fps Trem:   0min  62mb  A-V:-0.083 [7871:1797]

1 duplicate frame(s)!
Pos:  37.5s    821f (68%) 466.74fps Trem:   0min  63mb  A-V:-0.083 [7844:1799]

1 duplicate frame(s)!
Pos:  38.0s    831f (68%) 472.16fps Trem:   0min  63mb  A-V:-0.083 [7818:1799]

1 duplicate frame(s)!
Pos:  38.5s    841f (68%) 470.88fps Trem:   0min  64mb  A-V:-0.083 [7778:1799]

1 duplicate frame(s)!
Pos:  38.9s    851f (68%) 476.22fps Trem:   0min  64mb  A-V:-0.083 [7740:1801]

1 duplicate frame(s)!
Pos:  39.4s    861f (68%) 481.54fps Trem:   0min  65mb  A-V:-0.083 [7714:1803]

1 duplicate frame(s)!
Pos:  39.8s    871f (68%) 486.86fps Trem:   0min  65mb  A-V:-0.083 [7688:1804]

1 duplicate frame(s)!
Pos:  40.3s    881f (68%) 481.68fps Trem:   0min  66mb  A-V:-0.083 [7652:1806]

1 duplicate frame(s)!
Pos:  40.7s    891f (68%) 486.89fps Trem:   0min  66mb  A-V:-0.083 [7612:1806]

1 duplicate frame(s)!
Pos:  41.2s    901f (68%) 492.08fps Trem:   0min  67mb  A-V:-0.083 [7585:1806]

1 duplicate frame(s)!
Pos:  41.7s    911f (68%) 490.84fps Trem:   0min  68mb  A-V:-0.083 [7594:1806]

1 duplicate frame(s)!
Pos:  42.1s    921f (68%) 495.96fps Trem:   0min  68mb  A-V:-0.083 [7583:1805]

1 duplicate frame(s)!
Pos:  42.6s    931f (68%) 501.08fps Trem:   0min  69mb  A-V:-0.083 [7557:1803]

1 duplicate frame(s)!
Pos:  43.0s    941f (68%) 499.47fps Trem:   0min  69mb  A-V:-0.083 [7517:1802]

1 duplicate frame(s)!
Pos:  43.5s    951f (68%) 504.51fps Trem:   0min  69mb  A-V:-0.083 [7462:1801]

1 duplicate frame(s)!
Pos:  44.0s    961f (68%) 509.54fps Trem:   0min  70mb  A-V:-0.083 [7416:1800]

1 duplicate frame(s)!
Pos:  44.4s    971f (69%) 509.44fps Trem:   0min  70mb  A-V:-0.083 [7370:1799]

1 duplicate frame(s)!
Pos:  44.9s    981f (69%) 514.42fps Trem:   0min  70mb  A-V:-0.083 [7333:1798]

1 duplicate frame(s)!
Pos:  45.3s    991f (69%) 512.67fps Trem:   0min  71mb  A-V:-0.083 [7297:1796]

1 duplicate frame(s)!
Pos:  45.8s   1001f (69%) 517.58fps Trem:   0min  71mb  A-V:-0.083 [7268:1795]

1 duplicate frame(s)!
Pos:  46.3s   1011f (69%) 515.82fps Trem:   0min  72mb  A-V:-0.083 [7302:1795]

1 duplicate frame(s)!
Pos:  46.7s   1021f (69%) 520.65fps Trem:   0min  73mb  A-V:-0.083 [7311:1793]

1 duplicate frame(s)!
Pos:  47.2s   1031f (69%) 525.48fps Trem:   0min  74mb  A-V:-0.083 [7320:1792]

1 duplicate frame(s)!
Pos:  47.6s   1041f (69%) 522.33fps Trem:   0min  74mb  A-V:-0.083 [7312:1791]

1 duplicate frame(s)!
Pos:  48.1s   1051f (69%) 527.08fps Trem:   0min  75mb  A-V:-0.083 [7317:1791]

1 duplicate frame(s)!
Pos:  48.5s   1061f (69%) 524.21fps Trem:   0min  76mb  A-V:-0.083 [7318:1790]

1 duplicate frame(s)!
Pos:  49.0s   1071f (69%) 528.89fps Trem:   0min  77mb  A-V:-0.083 [7350:1789]

1 duplicate frame(s)!
Pos:  49.5s   1081f (69%) 517.72fps Trem:   0min  77mb  A-V:-0.083 [7342:1787]

1 duplicate frame(s)!
Pos:  49.9s   1091f (69%) 522.26fps Trem:   0min  78mb  A-V:-0.083 [7318:1785]

1 duplicate frame(s)!
Pos:  50.4s   1101f (69%) 521.06fps Trem:   0min  78mb  A-V:-0.083 [7358:1784]

1 duplicate frame(s)!
Pos:  50.8s   1111f (69%) 525.54fps Trem:   0min  79mb  A-V:-0.083 [7351:1783]

1 duplicate frame(s)!
Pos:  51.3s   1121f (69%) 517.07fps Trem:   0min  80mb  A-V:-0.083 [7350:1782]

1 duplicate frame(s)!
Pos:  51.8s   1131f (69%) 521.44fps Trem:   0min  80mb  A-V:-0.083 [7354:1781]

1 duplicate frame(s)!
Pos:  52.2s   1141f (69%) 525.81fps Trem:   0min  81mb  A-V:-0.083 [7356:1780]

1 duplicate frame(s)!
Pos:  52.7s   1151f (69%) 524.13fps Trem:   0min  82mb  A-V:-0.083 [7362:1780]

1 duplicate frame(s)!
Pos:  53.1s   1161f (69%) 528.21fps Trem:   0min  83mb  A-V:-0.083 [7368:1780]

1 duplicate frame(s)!
Pos:  53.6s   1171f (70%) 526.77fps Trem:   0min  83mb  A-V:-0.083 [7388:1779]

1 duplicate frame(s)!
Pos:  54.1s   1181f (70%) 531.03fps Trem:   0min  84mb  A-V:-0.083 [7403:1779]

1 duplicate frame(s)!
Pos:  54.5s   1191f (70%) 522.14fps Trem:   0min  85mb  A-V:-0.083 [7397:1779]

1 duplicate frame(s)!
Pos:  55.0s   1201f (70%) 526.06fps Trem:   0min  86mb  A-V:-0.083 [7455:1779]

1 duplicate frame(s)!
Pos:  55.4s   1211f (70%) 524.92fps Trem:   0min  87mb  A-V:-0.083 [7461:1779]

1 duplicate frame(s)!
Pos:  55.9s   1221f (70%) 529.03fps Trem:   0min  87mb  A-V:-0.083 [7468:1779]

1 duplicate frame(s)!
Pos:  56.3s   1231f (70%) 533.13fps Trem:   0min  88mb  A-V:-0.083 [7476:1780]

1 duplicate frame(s)!
Pos:  56.8s   1241f (70%) 532.16fps Trem:   0min  89mb  A-V:-0.083 [7490:1781]

1 duplicate frame(s)!
Pos:  57.3s   1251f (70%) 535.99fps Trem:   0min  90mb  A-V:-0.083 [7505:1782]

1 duplicate frame(s)!
Pos:  57.7s   1261f (70%) 497.04fps Trem:   0min  90mb  A-V:-0.083 [7509:1782]

1 duplicate frame(s)!
Pos:  58.2s   1271f (70%) 500.79fps Trem:   0min  91mb  A-V:-0.083 [7522:1783]

1 duplicate frame(s)!
Pos:  58.6s   1281f (70%) 501.37fps Trem:   0min  92mb  A-V:-0.083 [7531:1783]

1 duplicate frame(s)!
Pos:  59.1s   1291f (70%) 505.09fps Trem:   0min  93mb  A-V:-0.083 [7535:1784]

1 duplicate frame(s)!
Pos:  59.6s   1301f (70%) 401.92fps Trem:   0min  93mb  A-V:-0.083 [7533:1784]

1 duplicate frame(s)!
Pos:  60.0s   1311f (70%) 401.16fps Trem:   0min  94mb  A-V:-0.083 [7547:1783]

1 duplicate frame(s)!
Pos:  60.5s   1321f (70%) 400.18fps Trem:   0min  95mb  A-V:-0.083 [7574:1783]

1 duplicate frame(s)!
Pos:  60.9s   1331f (70%) 403.09fps Trem:   0min  96mb  A-V:-0.083 [7610:1783]

1 duplicate frame(s)!
Pos:  61.4s   1341f (70%) 400.66fps Trem:   0min  97mb  A-V:-0.083 [7653:1783]

1 duplicate frame(s)!
Pos:  61.9s   1351f (70%) 403.52fps Trem:   0min  98mb  A-V:-0.083 [7643:1783]

1 duplicate frame(s)!
Pos:  62.3s   1361f (71%) 403.26fps Trem:   0min  98mb  A-V:-0.083 [7623:1783]

1 duplicate frame(s)!
Pos:  62.8s   1371f (71%) 406.10fps Trem:   0min  99mb  A-V:-0.083 [7648:1782]

1 duplicate frame(s)!
Pos:  63.2s   1381f (71%) 408.94fps Trem:   0min 100mb  A-V:-0.083 [7653:1782]

1 duplicate frame(s)!
Pos:  63.7s   1391f (71%) 408.76fps Trem:   0min 100mb  A-V:-0.083 [7651:1783]

1 duplicate frame(s)!
Pos:  64.1s   1401f (71%) 411.45fps Trem:   0min 102mb  A-V:-0.083 [7697:1783]

1 duplicate frame(s)!
Pos:  64.6s   1411f (71%) 414.27fps Trem:   0min 102mb  A-V:-0.083 [7694:1783]

1 duplicate frame(s)!
Pos:  65.1s   1421f (71%) 412.36fps Trem:   0min 103mb  A-V:-0.083 [7688:1783]

1 duplicate frame(s)!
Pos:  65.5s   1431f (71%) 415.02fps Trem:   0min 104mb  A-V:-0.083 [7723:1782]

1 duplicate frame(s)!
Pos:  66.0s   1441f (71%) 417.80fps Trem:   0min 105mb  A-V:-0.083 [7737:1783]

1 duplicate frame(s)!
Pos:  66.4s   1451f (71%) 414.57fps Trem:   0min 105mb  A-V:-0.083 [7735:1783]

1 duplicate frame(s)!
Pos:  66.9s   1461f (71%) 417.31fps Trem:   0min 106mb  A-V:-0.083 [7746:1783]

1 duplicate frame(s)!
Pos:  67.4s   1471f (71%) 420.05fps Trem:   0min 107mb  A-V:-0.083 [7752:1783]

1 duplicate frame(s)!
Pos:  67.8s   1481f (71%) 420.98fps Trem:   0min 108mb  A-V:-0.083 [7749:1784]

1 duplicate frame(s)!
Pos:  68.3s   1491f (71%) 420.36fps Trem:   0min 108mb  A-V:-0.083 [7758:1785]

1 duplicate frame(s)!
Pos:  68.7s   1501f (71%) 423.06fps Trem:   0min 109mb  A-V:-0.083 [7762:1785]

1 duplicate frame(s)!
Pos:  69.2s   1511f (71%) 422.18fps Trem:   0min 109mb  A-V:-0.083 [7751:1786]

1 duplicate frame(s)!
Pos:  69.7s   1521f (71%) 424.86fps Trem:   0min 110mb  A-V:-0.083 [7751:1786]

1 duplicate frame(s)!
Pos:  70.1s   1531f (71%) 420.84fps Trem:   0min 111mb  A-V:-0.083 [7749:1786]

1 duplicate frame(s)!
Pos:  70.6s   1541f (71%) 423.58fps Trem:   0min 111mb  A-V:-0.083 [7741:1786]

1 duplicate frame(s)!
Pos:  71.0s   1551f (71%) 426.10fps Trem:   0min 112mb  A-V:-0.083 [7733:1786]

1 duplicate frame(s)!
Pos:  71.5s   1561f (71%) 425.80fps Trem:   0min 112mb  A-V:-0.083 [7729:1785]

1 duplicate frame(s)!
Pos:  71.9s   1571f (71%) 428.42fps Trem:   0min 113mb  A-V:-0.083 [7719:1785]

1 duplicate frame(s)!
Pos:  72.4s   1581f (71%) 431.03fps Trem:   0min 114mb  A-V:-0.083 [7716:1785]

1 duplicate frame(s)!
Pos:  72.9s   1591f (72%) 426.66fps Trem:   0min 114mb  A-V:-0.083 [7703:1785]

1 duplicate frame(s)!
Pos:  73.3s   1601f (72%) 429.22fps Trem:   0min 115mb  A-V:-0.083 [7696:1786]

1 duplicate frame(s)!
Pos:  73.8s   1611f (72%) 431.79fps Trem:   0min 115mb  A-V:-0.083 [7689:1786]

1 duplicate frame(s)!
Pos:  74.2s   1621f (72%) 413.41fps Trem:   0min 116mb  A-V:-0.083 [7681:1787]

1 duplicate frame(s)!
Pos:  74.7s   1631f (72%) 415.86fps Trem:   0min 116mb  A-V:-0.083 [7665:1787]

1 duplicate frame(s)!
Pos:  75.2s   1641f (72%) 415.76fps Trem:   0min 117mb  A-V:-0.083 [7667:1787]

1 duplicate frame(s)!
Pos:  75.6s   1651f (72%) 418.08fps Trem:   0min 118mb  A-V:-0.083 [7721:1788]

1 duplicate frame(s)!
Pos:  76.1s   1661f (72%) 418.49fps Trem:   0min 119mb  A-V:-0.083 [7725:1789]

1 duplicate frame(s)!
Pos:  76.5s   1671f (72%) 420.91fps Trem:   0min 120mb  A-V:-0.083 [7736:1789]

1 duplicate frame(s)!
Pos:  77.0s   1681f (72%) 423.21fps Trem:   0min 121mb  A-V:-0.083 [7749:1790]

1 duplicate frame(s)!
Pos:  77.5s   1691f (72%) 422.43fps Trem:   0min 121mb  A-V:-0.083 [7747:1791]

1 duplicate frame(s)!
Pos:  77.9s   1701f (72%) 421.25fps Trem:   0min 122mb  A-V:-0.083 [7755:1791]

1 duplicate frame(s)!
Pos:  78.4s   1711f (72%) 423.62fps Trem:   0min 123mb  A-V:-0.083 [7759:1792]

1 duplicate frame(s)!
Pos:  78.8s   1721f (72%) 423.68fps Trem:   0min 123mb  A-V:-0.083 [7769:1793]

1 duplicate frame(s)!
Pos:  79.3s   1731f (72%) 426.04fps Trem:   0min 124mb  A-V:-0.083 [7753:1793]

1 duplicate frame(s)!
Pos:  79.7s   1741f (72%) 425.98fps Trem:   0min 124mb  A-V:-0.083 [7730:1794]

1 duplicate frame(s)!
Pos:  80.2s   1751f (72%) 428.33fps Trem:   0min 125mb  A-V:-0.083 [7710:1794]

1 duplicate frame(s)!
Pos:  80.7s   1761f (72%) 430.67fps Trem:   0min 125mb  A-V:-0.083 [7688:1794]

1 duplicate frame(s)!
Pos:  81.1s   1771f (72%) 433.01fps Trem:   0min 126mb  A-V:-0.083 [7701:1795]

1 duplicate frame(s)!
Pos:  81.6s   1781f (72%) 435.03fps Trem:   0min 127mb  A-V:-0.083 [7724:1795]

1 duplicate frame(s)!
Pos:  82.0s   1791f (72%) 402.02fps Trem:   0min 127mb  A-V:-0.083 [7734:1796]

1 duplicate frame(s)!
Pos:  82.5s   1801f (72%) 404.17fps Trem:   0min 128mb  A-V:-0.083 [7743:1796]

1 duplicate frame(s)!
Pos:  83.0s   1811f (72%) 406.33fps Trem:   0min 129mb  A-V:-0.083 [7746:1796]

1 duplicate frame(s)!
Pos:  83.4s   1821f (73%) 402.16fps Trem:   0min 129mb  A-V:-0.083 [7737:1796]

1 duplicate frame(s)!
Pos:  83.9s   1831f (73%) 404.28fps Trem:   0min 130mb  A-V:-0.083 [7739:1797]

1 duplicate frame(s)!
Pos:  84.3s   1841f (73%) 406.40fps Trem:   0min 131mb  A-V:-0.083 [7733:1797]

1 duplicate frame(s)!
Pos:  84.8s   1851f (73%) 408.52fps Trem:   0min 132mb  A-V:-0.083 [7732:1797]

1 duplicate frame(s)!
Pos:  85.3s   1861f (73%) 408.74fps Trem:   0min 132mb  A-V:-0.083 [7744:1797]

1 duplicate frame(s)!
Pos:  85.7s   1871f (73%) 410.85fps Trem:   0min 133mb  A-V:-0.083 [7777:1797]

1 duplicate frame(s)!
Pos:  86.2s   1881f (73%) 412.86fps Trem:   0min 135mb  A-V:-0.083 [7812:1798]

1 duplicate frame(s)!
Pos:  86.6s   1891f (73%) 412.88fps Trem:   0min 135mb  A-V:-0.083 [7818:1798]

1 duplicate frame(s)!
Pos:  87.1s   1901f (73%) 414.97fps Trem:   0min 136mb  A-V:-0.083 [7824:1798]

1 duplicate frame(s)!
Pos:  87.5s   1911f (73%) 416.98fps Trem:   0min 137mb  A-V:-0.083 [7850:1799]

1 duplicate frame(s)!
Pos:  88.0s   1921f (73%) 419.07fps Trem:   0min 138mb  A-V:-0.083 [7857:1799]

1 duplicate frame(s)!
Pos:  88.5s   1931f (73%) 419.14fps Trem:   0min 138mb  A-V:-0.083 [7853:1799]

1 duplicate frame(s)!
Pos:  88.9s   1941f (73%) 421.32fps Trem:   0min 139mb  A-V:-0.083 [7832:1799]

1 duplicate frame(s)!
Pos:  89.4s   1951f (73%) 423.39fps Trem:   0min 139mb  A-V:-0.083 [7816:1799]

1 duplicate frame(s)!
Pos:  89.8s   1961f (73%) 425.47fps Trem:   0min 140mb  A-V:-0.083 [7800:1799]

1 duplicate frame(s)!
Pos:  90.3s   1971f (73%) 427.55fps Trem:   0min 140mb  A-V:-0.083 [7789:1798]

1 duplicate frame(s)!
Pos:  90.8s   1981f (73%) 428.32fps Trem:   0min 141mb  A-V:-0.083 [7778:1798]

1 duplicate frame(s)!
Pos:  91.2s   1991f (73%) 430.39fps Trem:   0min 141mb  A-V:-0.083 [7763:1798]

1 duplicate frame(s)!
Pos:  91.7s   2001f (73%) 432.46fps Trem:   0min 142mb  A-V:-0.083 [7751:1797]

1 duplicate frame(s)!
Pos:  92.1s   2011f (73%) 432.10fps Trem:   0min 142mb  A-V:-0.083 [7735:1797]

1 duplicate frame(s)!
Pos:  92.6s   2021f (73%) 434.25fps Trem:   0min 142mb  A-V:-0.083 [7717:1796]

1 duplicate frame(s)!
Pos:  93.1s   2031f (73%) 436.31fps Trem:   0min 143mb  A-V:-0.083 [7701:1795]

1 duplicate frame(s)!
Pos:  93.5s   2041f (73%) 438.36fps Trem:   0min 143mb  A-V:-0.083 [7690:1794]

1 duplicate frame(s)!
Pos:  94.0s   2051f (73%) 430.16fps Trem:   0min 144mb  A-V:-0.083 [7676:1794]

1 duplicate frame(s)!
Pos:  94.4s   2061f (73%) 432.17fps Trem:   0min 144mb  A-V:-0.083 [7663:1794]

1 duplicate frame(s)!
Pos:  94.9s   2071f (73%) 434.17fps Trem:   0min 145mb  A-V:-0.083 [7650:1793]

1 duplicate frame(s)!
Pos:  95.3s   2081f (73%) 436.18fps Trem:   0min 145mb  A-V:-0.083 [7634:1791]

1 duplicate frame(s)!
Pos:  95.8s   2091f (73%) 438.27fps Trem:   0min 146mb  A-V:-0.083 [7620:1789]

1 duplicate frame(s)!
Pos:  96.3s   2101f (73%) 440.28fps Trem:   0min 146mb  A-V:-0.083 [7604:1788]

1 duplicate frame(s)!
Pos:  96.7s   2111f (73%) 442.28fps Trem:   0min 146mb  A-V:-0.083 [7588:1786]

1 duplicate frame(s)!
Pos:  97.2s   2121f (73%) 444.37fps Trem:   0min 147mb  A-V:-0.083 [7574:1783]

1 duplicate frame(s)!
Pos:  97.6s   2131f (73%) 446.38fps Trem:   0min 147mb  A-V:-0.083 [7556:1780]

1 duplicate frame(s)!
Pos:  98.1s   2141f (73%) 448.38fps Trem:   0min 148mb  A-V:-0.083 [7539:1777]

1 duplicate frame(s)!
Pos:  98.6s   2151f (73%) 448.22fps Trem:   0min 148mb  A-V:-0.083 [7521:1775]

1 duplicate frame(s)!
Pos:  99.0s   2161f (73%) 450.30fps Trem:   0min 148mb  A-V:-0.083 [7501:1774]

1 duplicate frame(s)!
Pos:  99.5s   2171f (73%) 452.29fps Trem:   0min 148mb  A-V:-0.083 [7479:1770]

1 duplicate frame(s)!
Pos:  99.9s   2181f (73%) 454.28fps Trem:   0min 149mb  A-V:-0.083 [7454:1767]

1 duplicate frame(s)!
Pos: 100.4s   2191f (74%) 451.85fps Trem:   0min 148mb  A-V:-0.083 [7430:1765]

1 duplicate frame(s)!
Pos: 100.9s   2201f (74%) 451.39fps Trem:   0min 148mb  A-V:-0.083 [7408:1763]

1 duplicate frame(s)!
Pos: 101.3s   2211f (74%) 443.17fps Trem:   0min 149mb  A-V:-0.083 [7391:1762]

1 duplicate frame(s)!
Pos: 101.8s   2221f (74%) 439.11fps Trem:   0min 149mb  A-V:-0.083 [7374:1762]

1 duplicate frame(s)!
Pos: 102.2s   2231f (74%) 438.66fps Trem:   0min 149mb  A-V:-0.083 [7359:1762]

1 duplicate frame(s)!
Pos: 102.7s   2241f (74%) 434.81fps Trem:   0min 149mb  A-V:-0.083 [7351:1761]

1 duplicate frame(s)!
Pos: 103.1s   2251f (74%) 433.97fps Trem:   0min 149mb  A-V:-0.083 [7345:1761]

1 duplicate frame(s)!
Pos: 103.6s   2261f (75%) 429.36fps Trem:   0min 149mb  A-V:-0.083 [7334:1761]

1 duplicate frame(s)!
Pos: 104.1s   2271f (75%) 429.38fps Trem:   0min 149mb  A-V:-0.083 [7329:1760]

1 duplicate frame(s)!
Pos: 104.5s   2281f (75%) 424.61fps Trem:   0min 149mb  A-V:-0.083 [7297:1760]

1 duplicate frame(s)!
Pos: 105.0s   2291f (75%) 415.79fps Trem:   0min 149mb  A-V:-0.083 [7265:1759]

1 duplicate frame(s)!
Pos: 105.4s   2301f (75%) 415.72fps Trem:   0min 149mb  A-V:-0.083 [7233:1759]

1 duplicate frame(s)!
Pos: 105.9s   2311f (75%) 415.57fps Trem:   0min 149mb  A-V:-0.083 [7202:1758]

1 duplicate frame(s)!
Pos: 106.4s   2321f (76%) 415.65fps Trem:   0min 149mb  A-V:-0.083 [7171:1758]

1 duplicate frame(s)!
Pos: 106.8s   2331f (76%) 405.67fps Trem:   0min 149mb  A-V:-0.083 [7140:1757]

1 duplicate frame(s)!
Pos: 107.3s   2341f (76%) 405.30fps Trem:   0min 148mb  A-V:-0.083 [7110:1757]

1 duplicate frame(s)!
Pos: 107.7s   2350f (76%) 406.79fps Trem:   0min 148mb  A-V:-0.079 [7082:1756]

Too many video packets in the buffer: (235 in 33609791 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Pos: 107.7s   2351f (76%) 406.96fps Trem:   0min 148mb  A-V:-0.083 [7079:1756]

1 duplicate frame(s)!
Pos: 108.2s   2361f (76%) 408.69fps Trem:   0min 148mb  A-V:-0.083 [7049:1756]

1 duplicate frame(s)!
Pos: 108.7s   2371f (76%) 410.42fps Trem:   0min 148mb  A-V:-0.083 [7020:1756]

1 duplicate frame(s)!
Pos: 109.1s   2381f (76%) 412.15fps Trem:   0min 148mb  A-V:-0.083 [6990:1756]

1 duplicate frame(s)!
Pos: 109.6s   2391f (76%) 413.81fps Trem:   0min 149mb  A-V:-0.083 [6981:1756]

1 duplicate frame(s)!
Pos: 110.0s   2401f (76%) 415.54fps Trem:   0min 149mb  A-V:-0.083 [6966:1756]

1 duplicate frame(s)!
Pos: 110.5s   2411f (76%) 417.06fps Trem:   0min 151mb  A-V:-0.083 [7086:1756]

1 duplicate frame(s)!
Pos: 110.9s   2421f (76%) 418.64fps Trem:   0min 154mb  A-V:-0.083 [7196:1756]

1 duplicate frame(s)!
Pos: 111.4s   2431f (76%) 420.22fps Trem:   0min 155mb  A-V:-0.083 [7258:1756]

1 duplicate frame(s)!
Pos: 111.9s   2441f (76%) 421.88fps Trem:   0min 157mb  A-V:-0.083 [7330:1756]

1 duplicate frame(s)!
Pos: 112.3s   2451f (76%) 423.39fps Trem:   0min 160mb  A-V:-0.083 [7445:1756]

1 duplicate frame(s)!
Pos: 112.8s   2461f (76%) 424.97fps Trem:   0min 162mb  A-V:-0.083 [7567:1756]

1 duplicate frame(s)!
Pos: 113.2s   2471f (76%) 426.55fps Trem:   0min 165mb  A-V:-0.083 [7696:1756]

1 duplicate frame(s)!
Pos: 113.7s   2481f (76%) 428.13fps Trem:   0min 168mb  A-V:-0.083 [7802:1756]

1 duplicate frame(s)!
Pos: 114.2s   2491f (76%) 429.41fps Trem:   0min 170mb  A-V:-0.083 [7903:1756]

1 duplicate frame(s)!
Pos: 114.6s   2501f (76%) 430.98fps Trem:   0min 173mb  A-V:-0.083 [8013:1756]

1 duplicate frame(s)!
Pos: 115.1s   2511f (76%) 432.56fps Trem:   0min 175mb  A-V:-0.083 [8122:1756]

1 duplicate frame(s)!
Pos: 115.5s   2521f (76%) 434.06fps Trem:   0min 178mb  A-V:-0.083 [8227:1756]

1 duplicate frame(s)!
Pos: 116.0s   2531f (76%) 435.63fps Trem:   0min 180mb  A-V:-0.083 [8307:1756]

1 duplicate frame(s)!
Pos: 116.4s   2541f (76%) 437.27fps Trem:   0min 181mb  A-V:-0.083 [8351:1756]

1 duplicate frame(s)!
Pos: 116.9s   2551f (76%) 438.84fps Trem:   0min 183mb  A-V:-0.083 [8420:1756]

1 duplicate frame(s)!
Pos: 117.4s   2561f (76%) 440.41fps Trem:   0min 185mb  A-V:-0.083 [8507:1756]

1 duplicate frame(s)!
Pos: 117.8s   2571f (76%) 441.98fps Trem:   0min 187mb  A-V:-0.083 [8590:1756]

1 duplicate frame(s)!
Pos: 118.3s   2581f (76%) 443.55fps Trem:   0min 189mb  A-V:-0.083 [8675:1756]

1 duplicate frame(s)!
Pos: 118.7s   2591f (76%) 444.96fps Trem:   0min 192mb  A-V:-0.083 [8759:1756]

1 duplicate frame(s)!
Pos: 119.0s   2595f (76%) 443.67fps Trem:   0min 192mb  A-V:-0.058 [8790:1756]

Too many video packets in the buffer: (190 in 33587703 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Pos: 119.2s   2601f (79%) 358.86fps Trem:   0min 189mb  A-V:-0.083 [8843:1751]

1 duplicate frame(s)!
Pos: 119.7s   2611f (79%) 360.14fps Trem:   0min 191mb  A-V:-0.083 [8915:1751]

1 duplicate frame(s)!
Pos: 120.1s   2621f (79%) 361.42fps Trem:   0min 193mb  A-V:-0.083 [8992:1751]

1 duplicate frame(s)!
Pos: 120.6s   2631f (79%) 362.70fps Trem:   0min 195mb  A-V:-0.083 [9076:1751]

1 duplicate frame(s)!
Pos: 121.0s   2641f (79%) 363.97fps Trem:   0min 197mb  A-V:-0.083 [9152:1751]

1 duplicate frame(s)!
Pos: 121.5s   2651f (79%) 365.25fps Trem:   0min 199mb  A-V:-0.083 [9236:1751]

1 duplicate frame(s)!
Pos: 122.0s   2661f (79%) 366.53fps Trem:   0min 201mb  A-V:-0.083 [9317:1751]

1 duplicate frame(s)!
Pos: 122.4s   2671f (79%) 367.80fps Trem:   0min 204mb  A-V:-0.083 [9403:1751]

1 duplicate frame(s)!
Pos: 122.9s   2681f (79%) 369.08fps Trem:   0min 206mb  A-V:-0.083 [9486:1751]

1 duplicate frame(s)!
Pos: 123.3s   2691f (79%) 370.36fps Trem:   0min 208mb  A-V:-0.083 [9566:1751]

1 duplicate frame(s)!
Pos: 123.8s   2701f (79%) 371.63fps Trem:   0min 210mb  A-V:-0.083 [9641:1751]

1 duplicate frame(s)!
Pos: 124.2s   2711f (79%) 372.90fps Trem:   0min 212mb  A-V:-0.083 [9725:1751]

1 duplicate frame(s)!
Pos: 124.7s   2721f (79%) 374.17fps Trem:   0min 215mb  A-V:-0.083 [9810:1751]

1 duplicate frame(s)!
Pos: 125.2s   2731f (79%) 375.45fps Trem:   0min 217mb  A-V:-0.083 [9893:1751]

1 duplicate frame(s)!
Pos: 125.6s   2741f (79%) 376.72fps Trem:   0min 219mb  A-V:-0.083 [9965:1751]

1 duplicate frame(s)!
Pos: 126.1s   2751f (79%) 370.01fps Trem:   0min 221mb  A-V:-0.083 [10043:1751]

1 duplicate frame(s)!
Pos: 126.5s   2761f (79%) 371.25fps Trem:   0min 223mb  A-V:-0.083 [10112:1751]

1 duplicate frame(s)!
Pos: 127.0s   2771f (79%) 372.50fps Trem:   0min 225mb  A-V:-0.083 [10199:1751]

1 duplicate frame(s)!
Pos: 127.5s   2781f (79%) 372.94fps Trem:   0min 227mb  A-V:-0.083 [10269:1751]

1 duplicate frame(s)!
Pos: 127.7s   2786f (79%) 373.56fps Trem:   0min 228mb  A-V:-0.063 [10300:1751]

Too many video packets in the buffer: (196 in 33621345 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Pos: 127.9s   2791f (81%) 313.49fps Trem:   0min 224mb  A-V:-0.083 [10339:1745]

1 duplicate frame(s)!
Pos: 128.4s   2801f (81%) 314.54fps Trem:   0min 226mb  A-V:-0.083 [10417:1745]

1 duplicate frame(s)!
Pos: 128.8s   2811f (81%) 315.63fps Trem:   0min 228mb  A-V:-0.083 [10481:1745]

1 duplicate frame(s)!
Pos: 129.3s   2821f (81%) 316.68fps Trem:   0min 230mb  A-V:-0.083 [10556:1745]

1 duplicate frame(s)!
Pos: 129.8s   2831f (81%) 317.73fps Trem:   0min 233mb  A-V:-0.083 [10633:1745]

1 duplicate frame(s)!
Pos: 130.2s   2841f (81%) 318.78fps Trem:   0min 234mb  A-V:-0.083 [10695:1745]

1 duplicate frame(s)!
Pos: 130.7s   2851f (81%) 319.83fps Trem:   0min 237mb  A-V:-0.083 [10774:1745]

1 duplicate frame(s)!
Pos: 131.1s   2861f (81%) 320.88fps Trem:   0min 239mb  A-V:-0.083 [10847:1745]

1 duplicate frame(s)!
Pos: 131.6s   2871f (81%) 321.93fps Trem:   0min 241mb  A-V:-0.083 [10909:1745]

1 duplicate frame(s)!
Pos: 132.0s   2881f (81%) 322.95fps Trem:   0min 243mb  A-V:-0.083 [10981:1745]

1 duplicate frame(s)!
Pos: 132.5s   2891f (81%) 323.99fps Trem:   0min 245mb  A-V:-0.083 [11038:1745]

1 duplicate frame(s)!
Pos: 133.0s   2901f (81%) 325.04fps Trem:   0min 247mb  A-V:-0.083 [11100:1745]

1 duplicate frame(s)!
Pos: 133.4s   2911f (81%) 326.05fps Trem:   0min 249mb  A-V:-0.083 [11166:1745]

1 duplicate frame(s)!
Pos: 133.9s   2921f (81%) 327.10fps Trem:   0min 251mb  A-V:-0.083 [11226:1745]

1 duplicate frame(s)!
Pos: 134.3s   2931f (81%) 328.15fps Trem:   0min 252mb  A-V:-0.083 [11284:1745]

1 duplicate frame(s)!
Pos: 134.8s   2941f (81%) 329.19fps Trem:   0min 254mb  A-V:-0.083 [11345:1745]

1 duplicate frame(s)!
Pos: 135.3s   2951f (81%) 330.24fps Trem:   0min 256mb  A-V:-0.083 [11403:1745]

1 duplicate frame(s)!
Pos: 135.7s   2961f (81%) 331.28fps Trem:   0min 258mb  A-V:-0.083 [11458:1745]

1 duplicate frame(s)!
Pos: 136.2s   2971f (81%) 332.29fps Trem:   0min 260mb  A-V:-0.083 [11533:1745]

1 duplicate frame(s)!
Pos: 136.6s   2981f (81%) 333.33fps Trem:   0min 262mb  A-V:-0.083 [11586:1745]

1 duplicate frame(s)!
Pos: 137.0s   2988f (81%) 331.71fps Trem:   0min 263mb  A-V:-0.071 [11625:1745]

Too many video packets in the buffer: (209 in 33587229 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Pos: 137.1s   2991f (84%) 292.29fps Trem:   0min 258mb  A-V:-0.083 [11647:1741]

1 duplicate frame(s)!
Pos: 137.6s   3001f (84%) 293.21fps Trem:   0min 260mb  A-V:-0.083 [11699:1741]

1 duplicate frame(s)!
Pos: 138.0s   3011f (84%) 294.13fps Trem:   0min 261mb  A-V:-0.083 [11756:1741]

1 duplicate frame(s)!
Pos: 138.5s   3021f (84%) 295.05fps Trem:   0min 263mb  A-V:-0.083 [11810:1741]

1 duplicate frame(s)!
Pos: 138.9s   3031f (84%) 295.97fps Trem:   0min 265mb  A-V:-0.083 [11863:1741]

1 duplicate frame(s)!
Pos: 139.4s   3041f (84%) 296.89fps Trem:   0min 267mb  A-V:-0.083 [11917:1741]

1 duplicate frame(s)!
Pos: 139.8s   3051f (84%) 297.80fps Trem:   0min 269mb  A-V:-0.083 [11966:1741]

1 duplicate frame(s)!
Pos: 140.3s   3061f (84%) 298.75fps Trem:   0min 271mb  A-V:-0.083 [12024:1741]

1 duplicate frame(s)!
Pos: 140.8s   3071f (84%) 299.67fps Trem:   0min 272mb  A-V:-0.083 [12070:1741]

1 duplicate frame(s)!
Pos: 141.2s   3081f (84%) 300.59fps Trem:   0min 274mb  A-V:-0.083 [12116:1741]

1 duplicate frame(s)!
Pos: 141.7s   3091f (84%) 301.50fps Trem:   0min 276mb  A-V:-0.083 [12169:1741]

1 duplicate frame(s)!
Pos: 142.1s   3101f (84%) 302.42fps Trem:   0min 278mb  A-V:-0.083 [12216:1741]

1 duplicate frame(s)!
Pos: 142.6s   3111f (84%) 303.33fps Trem:   0min 279mb  A-V:-0.083 [12264:1741]

1 duplicate frame(s)!
Pos: 143.1s   3121f (84%) 304.25fps Trem:   0min 281mb  A-V:-0.083 [12314:1741]

1 duplicate frame(s)!
Pos: 143.5s   3131f (84%) 305.17fps Trem:   0min 283mb  A-V:-0.083 [12362:1741]

1 duplicate frame(s)!
Pos: 144.0s   3141f (84%) 305.72fps Trem:   0min 285mb  A-V:-0.083 [12415:1741]

1 duplicate frame(s)!
Pos: 144.4s   3151f (84%) 306.67fps Trem:   0min 287mb  A-V:-0.083 [12464:1741]

1 duplicate frame(s)!
Pos: 144.9s   3161f (84%) 307.58fps Trem:   0min 288mb  A-V:-0.083 [12514:1741]

1 duplicate frame(s)!
Pos: 145.4s   3171f (84%) 308.49fps Trem:   0min 290mb  A-V:-0.083 [12561:1741]

1 duplicate frame(s)!
Pos: 145.8s   3181f (84%) 309.41fps Trem:   0min 292mb  A-V:-0.083 [12621:1741]

1 duplicate frame(s)!
Pos: 146.3s   3191f (84%) 310.32fps Trem:   0min 294mb  A-V:-0.083 [12674:1741]

1 duplicate frame(s)!
Pos: 146.7s   3201f (84%) 311.23fps Trem:   0min 296mb  A-V:-0.083 [12720:1741]

1 duplicate frame(s)!
Pos: 146.9s   3205f (84%) 310.47fps Trem:   0min 296mb  A-V:-0.058 [12735:1741]

Too many video packets in the buffer: (200 in 33590402 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Pos: 147.2s   3211f (87%) 250.47fps Trem:   0min 290mb  A-V:-0.083 [12760:1738]

1 duplicate frame(s)!
Pos: 147.6s   3221f (87%) 251.21fps Trem:   0min 292mb  A-V:-0.083 [12814:1738]

1 duplicate frame(s)!
Pos: 148.1s   3231f (87%) 251.95fps Trem:   0min 294mb  A-V:-0.083 [12860:1738]

1 duplicate frame(s)!
Pos: 148.6s   3241f (87%) 252.71fps Trem:   0min 296mb  A-V:-0.083 [12900:1738]

1 duplicate frame(s)!
Pos: 149.0s   3251f (87%) 253.45fps Trem:   0min 297mb  A-V:-0.083 [12937:1738]

1 duplicate frame(s)!
Pos: 149.5s   3261f (87%) 254.19fps Trem:   0min 299mb  A-V:-0.083 [12983:1738]

1 duplicate frame(s)!
Pos: 149.9s   3271f (87%) 254.93fps Trem:   0min 301mb  A-V:-0.083 [13026:1738]

1 duplicate frame(s)!
Pos: 150.4s   3281f (87%) 255.69fps Trem:   0min 302mb  A-V:-0.083 [13068:1738]

1 duplicate frame(s)!
Pos: 150.9s   3291f (87%) 256.43fps Trem:   0min 304mb  A-V:-0.083 [13109:1738]

1 duplicate frame(s)!
Pos: 151.3s   3301f (87%) 257.17fps Trem:   0min 306mb  A-V:-0.083 [13145:1738]

1 duplicate frame(s)!
Pos: 151.8s   3311f (87%) 257.91fps Trem:   0min 307mb  A-V:-0.083 [13191:1738]

1 duplicate frame(s)!
Pos: 152.2s   3321f (87%) 258.64fps Trem:   0min 309mb  A-V:-0.083 [13234:1738]

1 duplicate frame(s)!
Pos: 152.7s   3331f (87%) 259.38fps Trem:   0min 311mb  A-V:-0.083 [13267:1738]

1 duplicate frame(s)!
Pos: 153.2s   3341f (87%) 260.12fps Trem:   0min 312mb  A-V:-0.083 [13307:1738]

1 duplicate frame(s)!
Pos: 153.6s   3351f (87%) 260.86fps Trem:   0min 314mb  A-V:-0.083 [13353:1738]

1 duplicate frame(s)!
Pos: 154.1s   3361f (87%) 261.60fps Trem:   0min 316mb  A-V:-0.083 [13385:1738]

1 duplicate frame(s)!
Pos: 154.5s   3371f (87%) 262.33fps Trem:   0min 318mb  A-V:-0.083 [13442:1738]

1 duplicate frame(s)!
Pos: 155.0s   3381f (87%) 263.05fps Trem:   0min 320mb  A-V:-0.083 [13527:1738]

1 duplicate frame(s)!
Pos: 155.4s   3391f (87%) 263.77fps Trem:   0min 323mb  A-V:-0.083 [13603:1738]

1 duplicate frame(s)!
Pos: 155.9s   3401f (87%) 264.48fps Trem:   0min 325mb  A-V:-0.083 [13681:1738]

1 duplicate frame(s)!
Pos: 156.3s   3409f (87%) 263.65fps Trem:   0min 327mb  A-V:-0.075 [13733:1738]

Too many video packets in the buffer: (166 in 33679292 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Pos: 156.4s   3411f (89%) 252.14fps Trem:   0min 319mb  A-V:-0.083 [13750:1738]

1 duplicate frame(s)!
Pos: 156.8s   3421f (89%) 252.85fps Trem:   0min 321mb  A-V:-0.083 [13805:1738]

1 duplicate frame(s)!
Pos: 157.3s   3431f (89%) 253.55fps Trem:   0min 323mb  A-V:-0.083 [13861:1738]

1 duplicate frame(s)!
Pos: 157.7s   3441f (89%) 254.25fps Trem:   0min 325mb  A-V:-0.083 [13920:1738]

1 duplicate frame(s)!
Pos: 158.2s   3451f (89%) 254.93fps Trem:   0min 327mb  A-V:-0.083 [13982:1738]

1 duplicate frame(s)!
Pos: 158.7s   3461f (89%) 255.63fps Trem:   0min 330mb  A-V:-0.083 [14041:1738]

1 duplicate frame(s)!
Pos: 159.1s   3471f (89%) 256.33fps Trem:   0min 332mb  A-V:-0.083 [14107:1738]

1 duplicate frame(s)!
Pos: 159.6s   3481f (89%) 257.03fps Trem:   0min 334mb  A-V:-0.083 [14167:1738]

1 duplicate frame(s)!
Pos: 160.0s   3491f (89%) 257.71fps Trem:   0min 336mb  A-V:-0.083 [14230:1738]

1 duplicate frame(s)!
Pos: 160.5s   3501f (89%) 258.41fps Trem:   0min 338mb  A-V:-0.083 [14290:1738]

1 duplicate frame(s)!
Pos: 161.0s   3511f (89%) 259.13fps Trem:   0min 341mb  A-V:-0.083 [14355:1738]

1 duplicate frame(s)!
Pos: 161.4s   3521f (89%) 259.81fps Trem:   0min 343mb  A-V:-0.083 [14414:1738]

1 duplicate frame(s)!
Pos: 161.9s   3531f (89%) 260.51fps Trem:   0min 345mb  A-V:-0.083 [14476:1738]

1 duplicate frame(s)!
Pos: 162.3s   3541f (89%) 261.21fps Trem:   0min 347mb  A-V:-0.083 [14541:1738]

1 duplicate frame(s)!
Pos: 162.8s   3551f (89%) 261.91fps Trem:   0min 349mb  A-V:-0.083 [14598:1738]

1 duplicate frame(s)!
Pos: 163.2s   3561f (89%) 262.59fps Trem:   0min 351mb  A-V:-0.083 [14657:1738]

1 duplicate frame(s)!
Pos: 163.7s   3571f (89%) 263.29fps Trem:   0min 354mb  A-V:-0.083 [14713:1738]

1 duplicate frame(s)!
Pos: 164.2s   3581f (89%) 263.95fps Trem:   0min 356mb  A-V:-0.083 [14770:1738]

1 duplicate frame(s)!
Pos: 164.4s   3585f (89%) 263.78fps Trem:   0min 356mb  A-V:-0.058 [14794:1738]

Too many video packets in the buffer: (189 in 33622213 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Pos: 164.6s   3591f (92%) 251.28fps Trem:   0min 349mb  A-V:-0.083 [14826:1738]

1 duplicate frame(s)!
Pos: 165.1s   3601f (92%) 251.92fps Trem:   0min 351mb  A-V:-0.083 [14875:1738]

1 duplicate frame(s)!
Pos: 165.5s   3611f (92%) 252.59fps Trem:   0min 353mb  A-V:-0.083 [14923:1738]

1 duplicate frame(s)!
Pos: 166.0s   3621f (92%) 253.25fps Trem:   0min 355mb  A-V:-0.083 [14971:1738]

1 duplicate frame(s)!
Pos: 166.5s   3631f (92%) 253.92fps Trem:   0min 357mb  A-V:-0.083 [15015:1738]

1 duplicate frame(s)!
Pos: 166.9s   3641f (92%) 254.58fps Trem:   0min 359mb  A-V:-0.083 [15069:1738]

1 duplicate frame(s)!
Pos: 167.4s   3651f (92%) 255.24fps Trem:   0min 361mb  A-V:-0.083 [15112:1738]

1 duplicate frame(s)!
Pos: 167.8s   3661f (92%) 255.91fps Trem:   0min 363mb  A-V:-0.083 [15161:1738]

1 duplicate frame(s)!
Pos: 168.3s   3671f (92%) 256.57fps Trem:   0min 364mb  A-V:-0.083 [15204:1738]

1 duplicate frame(s)!
Pos: 168.8s   3681f (92%) 257.23fps Trem:   0min 366mb  A-V:-0.083 [15248:1738]

1 duplicate frame(s)!
Pos: 169.2s   3691f (92%) 257.90fps Trem:   0min 368mb  A-V:-0.083 [15294:1738]

1 duplicate frame(s)!
Pos: 169.7s   3701f (92%) 258.56fps Trem:   0min 370mb  A-V:-0.083 [15333:1738]

1 duplicate frame(s)!
Pos: 170.1s   3711f (92%) 259.22fps Trem:   0min 372mb  A-V:-0.083 [15381:1738]

1 duplicate frame(s)!
Pos: 170.6s   3721f (92%) 259.88fps Trem:   0min 374mb  A-V:-0.083 [15418:1738]

1 duplicate frame(s)!
Pos: 171.0s   3731f (92%) 260.53fps Trem:   0min 375mb  A-V:-0.083 [15458:1738]

1 duplicate frame(s)!
Pos: 171.5s   3741f (92%) 261.19fps Trem:   0min 377mb  A-V:-0.083 [15494:1738]

1 duplicate frame(s)!
Pos: 172.0s   3751f (92%) 261.85fps Trem:   0min 379mb  A-V:-0.083 [15529:1738]

1 duplicate frame(s)!
Pos: 172.4s   3761f (92%) 262.51fps Trem:   0min 381mb  A-V:-0.083 [15572:1738]

1 duplicate frame(s)!
Pos: 172.9s   3771f (92%) 263.19fps Trem:   0min 382mb  A-V:-0.083 [15602:1738]

1 duplicate frame(s)!
Pos: 173.3s   3781f (94%) 231.72fps Trem:   0min 378mb  A-V:-0.083 [15629:1739]

1 duplicate frame(s)!
Pos: 173.8s   3791f (95%) 231.98fps Trem:   0min 379mb  A-V:-0.083 [15648:1739]

1 duplicate frame(s)!
Pos: 174.3s   3801f (95%) 232.24fps Trem:   0min 379mb  A-V:-0.083 [15658:1739]

1 duplicate frame(s)!
Pos: 174.7s   3811f (95%) 229.79fps Trem:   0min 380mb  A-V:-0.083 [15663:1739]

1 duplicate frame(s)!
Pos: 175.2s   3821f (95%) 229.26fps Trem:   0min 380mb  A-V:-0.083 [15666:1739]

1 duplicate frame(s)!
Pos: 175.6s   3831f (95%) 229.51fps Trem:   0min 381mb  A-V:-0.083 [15668:1739]

1 duplicate frame(s)!
Pos: 176.1s   3841f (95%) 229.77fps Trem:   0min 381mb  A-V:-0.083 [15666:1739]

1 duplicate frame(s)!
Pos: 176.6s   3851f (95%) 228.78fps Trem:   0min 382mb  A-V:-0.083 [15667:1740]

1 duplicate frame(s)!
Pos: 177.0s   3861f (95%) 228.37fps Trem:   0min 383mb  A-V:-0.083 [15669:1740]

1 duplicate frame(s)!
Pos: 177.5s   3871f (95%) 228.93fps Trem:   0min 384mb  A-V:-0.083 [15671:1740]

1 duplicate frame(s)!
Pos: 177.9s   3881f (96%) 229.22fps Trem:   0min 384mb  A-V:-0.083 [15662:1740]

1 duplicate frame(s)!
Pos: 178.4s   3891f (96%) 229.48fps Trem:   0min 384mb  A-V:-0.083 [15654:1740]

1 duplicate frame(s)!
Pos: 178.8s   3901f (96%) 229.69fps Trem:   0min 385mb  A-V:-0.083 [15643:1740]

1 duplicate frame(s)!
Pos: 179.3s   3911f (96%) 229.79fps Trem:   0min 385mb  A-V:-0.083 [15629:1740]

1 duplicate frame(s)!
Pos: 179.8s   3921f (96%) 229.54fps Trem:   0min 386mb  A-V:-0.083 [15618:1740]

1 duplicate frame(s)!
Pos: 180.2s   3931f (96%) 230.11fps Trem:   0min 386mb  A-V:-0.083 [15603:1740]

1 duplicate frame(s)!
Pos: 180.4s   3934f (96%) 230.29fps Trem:   0min 386mb  A-V:-0.054 [15597:1740]

Too many video packets in the buffer: (400 in 33582897 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Pos: 180.7s   3941f (96%) 230.68fps Trem:   0min 386mb  A-V:-0.083 [15589:1740]

1 duplicate frame(s)!
Pos: 181.1s   3951f (96%) 231.26fps Trem:   0min 387mb  A-V:-0.083 [15575:1740]

1 duplicate frame(s)!
Pos: 181.6s   3961f (96%) 231.83fps Trem:   0min 388mb  A-V:-0.083 [15573:1740]

1 duplicate frame(s)!
Pos: 182.1s   3971f (96%) 232.40fps Trem:   0min 388mb  A-V:-0.083 [15565:1740]

1 duplicate frame(s)!
Pos: 182.5s   3981f (96%) 232.97fps Trem:   0min 389mb  A-V:-0.083 [15554:1740]

1 duplicate frame(s)!
Pos: 183.0s   3991f (96%) 233.54fps Trem:   0min 390mb  A-V:-0.083 [15541:1740]

1 duplicate frame(s)!
Pos: 183.4s   4001f (96%) 234.13fps Trem:   0min 390mb  A-V:-0.083 [15526:1740]

1 duplicate frame(s)!
Pos: 183.9s   4011f (96%) 234.70fps Trem:   0min 391mb  A-V:-0.083 [15511:1740]

1 duplicate frame(s)!
Pos: 184.4s   4021f (96%) 235.27fps Trem:   0min 391mb  A-V:-0.083 [15496:1740]

1 duplicate frame(s)!
Pos: 184.8s   4031f (96%) 235.84fps Trem:   0min 392mb  A-V:-0.083 [15480:1740]

1 duplicate frame(s)!
Pos: 185.3s   4041f (96%) 236.41fps Trem:   0min 392mb  A-V:-0.083 [15465:1740]

1 duplicate frame(s)!
Pos: 185.7s   4051f (96%) 236.98fps Trem:   0min 393mb  A-V:-0.083 [15449:1740]

1 duplicate frame(s)!
Pos: 186.2s   4061f (96%) 237.57fps Trem:   0min 393mb  A-V:-0.083 [15435:1740]

1 duplicate frame(s)!
Pos: 186.6s   4071f (96%) 238.14fps Trem:   0min 394mb  A-V:-0.083 [15421:1740]

1 duplicate frame(s)!
Pos: 187.1s   4081f (96%) 238.71fps Trem:   0min 395mb  A-V:-0.083 [15410:1740]

1 duplicate frame(s)!
Pos: 187.6s   4091f (96%) 239.28fps Trem:   0min 395mb  A-V:-0.083 [15398:1740]

1 duplicate frame(s)!
Pos: 188.0s   4101f (96%) 239.85fps Trem:   0min 396mb  A-V:-0.083 [15384:1740]

1 duplicate frame(s)!
Pos: 188.5s   4111f (96%) 240.42fps Trem:   0min 396mb  A-V:-0.083 [15370:1740]

1 duplicate frame(s)!
Pos: 188.9s   4121f (96%) 240.99fps Trem:   0min 397mb  A-V:-0.083 [15356:1740]

1 duplicate frame(s)!
Pos: 189.4s   4131f (96%) 241.56fps Trem:   0min 397mb  A-V:-0.083 [15341:1740]

1 duplicate frame(s)!
Pos: 189.9s   4141f (96%) 242.14fps Trem:   0min 398mb  A-V:-0.083 [15328:1740]

1 duplicate frame(s)!
Pos: 190.3s   4151f (96%) 242.72fps Trem:   0min 398mb  A-V:-0.083 [15316:1740]

1 duplicate frame(s)!
Pos: 190.8s   4161f (96%) 243.28fps Trem:   0min 399mb  A-V:-0.083 [15312:1740]

1 duplicate frame(s)!
Pos: 191.2s   4171f (96%) 243.85fps Trem:   0min 400mb  A-V:-0.083 [15317:1740]

1 duplicate frame(s)!
Pos: 191.7s   4181f (96%) 244.40fps Trem:   0min 402mb  A-V:-0.083 [15339:1740]

1 duplicate frame(s)!
Pos: 192.2s   4191f (96%) 244.97fps Trem:   0min 403mb  A-V:-0.083 [15361:1740]

1 duplicate frame(s)!
Pos: 192.6s   4201f (96%) 245.53fps Trem:   0min 404mb  A-V:-0.083 [15384:1740]

1 duplicate frame(s)!
Pos: 193.1s   4211f (96%) 246.10fps Trem:   0min 406mb  A-V:-0.083 [15408:1740]

1 duplicate frame(s)!
Pos: 193.5s   4221f (96%) 246.65fps Trem:   0min 407mb  A-V:-0.083 [15430:1740]

1 duplicate frame(s)!
Pos: 194.0s   4231f (96%) 247.21fps Trem:   0min 409mb  A-V:-0.083 [15447:1740]

1 duplicate frame(s)!
Pos: 194.4s   4241f (96%) 247.69fps Trem:   0min 410mb  A-V:-0.083 [15463:1740]

1 duplicate frame(s)!
Pos: 194.9s   4251f (96%) 248.26fps Trem:   0min 411mb  A-V:-0.083 [15477:1740]

1 duplicate frame(s)!
Pos: 195.4s   4261f (96%) 248.83fps Trem:   0min 412mb  A-V:-0.083 [15489:1740]

1 duplicate frame(s)!
Pos: 195.8s   4271f (96%) 249.39fps Trem:   0min 413mb  A-V:-0.083 [15496:1740]

1 duplicate frame(s)!
Pos: 196.3s   4281f (96%) 249.96fps Trem:   0min 414mb  A-V:-0.083 [15504:1740]

1 duplicate frame(s)!
Pos: 196.7s   4291f (96%) 250.23fps Trem:   0min 415mb  A-V:-0.083 [15508:1740]

1 duplicate frame(s)!
Pos: 197.2s   4301f (96%) 250.80fps Trem:   0min 416mb  A-V:-0.083 [15510:1740]

1 duplicate frame(s)!
Pos: 197.7s   4311f (96%) 251.36fps Trem:   0min 417mb  A-V:-0.083 [15514:1740]

1 duplicate frame(s)!
Pos: 198.1s   4321f (96%) 251.92fps Trem:   0min 418mb  A-V:-0.083 [15516:1740]

1 duplicate frame(s)!
Pos: 198.6s   4331f (96%) 252.43fps Trem:   0min 419mb  A-V:-0.083 [15513:1740]

1 duplicate frame(s)!
Pos: 198.8s   4336f (96%) 252.72fps Trem:   0min 419mb  A-V:-0.063 [15508:1740]

Too many video packets in the buffer: (260 in 33679188 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Pos: 199.0s   4341f (99%) 221.28fps Trem:   0min 410mb  A-V:-0.083 [15507:1725]

1 duplicate frame(s)!
Pos: 199.5s   4351f (99%) 221.76fps Trem:   0min 411mb  A-V:-0.083 [15511:1725]

1 duplicate frame(s)!
Pos: 199.9s   4361f (99%) 222.26fps Trem:   0min 412mb  A-V:-0.083 [15512:1725]

1 duplicate frame(s)!
Pos: 200.4s   4371f (99%) 222.76fps Trem:   0min 413mb  A-V:-0.083 [15524:1725]

1 duplicate frame(s)!
Pos: 200.9s   4381f (99%) 223.25fps Trem:   0min 415mb  A-V:-0.083 [15556:1725]

1 duplicate frame(s)!
Pos: 201.3s   4391f (99%) 223.73fps Trem:   0min 416mb  A-V:-0.083 [15587:1725]

1 duplicate frame(s)!
Pos: 201.8s   4401f (99%) 224.22fps Trem:   0min 418mb  A-V:-0.083 [15617:1725]

1 duplicate frame(s)!
Pos: 202.2s   4411f (99%) 224.71fps Trem:   0min 420mb  A-V:-0.083 [15646:1725]

1 duplicate frame(s)!
Pos: 202.7s   4421f (99%) 225.19fps Trem:   0min 421mb  A-V:-0.083 [15671:1725]

1 duplicate frame(s)!
Pos: 203.2s   4431f (99%) 225.68fps Trem:   0min 422mb  A-V:-0.083 [15693:1725]

1 duplicate frame(s)!
Pos: 203.6s   4441f (99%) 226.17fps Trem:   0min 424mb  A-V:-0.083 [15705:1725]

1 duplicate frame(s)!
Pos: 204.1s   4451f (99%) 226.66fps Trem:   0min 425mb  A-V:-0.083 [15719:1725]

1 duplicate frame(s)!
Pos: 204.5s   4461f (99%) 227.15fps Trem:   0min 426mb  A-V:-0.083 [15743:1725]

1 duplicate frame(s)!
Pos: 205.0s   4471f (99%) 227.64fps Trem:   0min 427mb  A-V:-0.083 [15751:1725]

1 duplicate frame(s)!
Pos: 205.5s   4481f (99%) 228.12fps Trem:   0min 429mb  A-V:-0.083 [15765:1725]

1 duplicate frame(s)!
Pos: 205.9s   4491f (99%) 228.62fps Trem:   0min 430mb  A-V:-0.083 [15774:1725]

1 duplicate frame(s)!
Pos: 206.4s   4501f (99%) 229.11fps Trem:   0min 431mb  A-V:-0.083 [15786:1725]

1 duplicate frame(s)!
Pos: 206.8s   4511f (99%) 229.59fps Trem:   0min 432mb  A-V:-0.083 [15802:1725]

1 duplicate frame(s)!
Pos: 207.3s   4521f (99%) 230.08fps Trem:   0min 434mb  A-V:-0.083 [15830:1725]

1 duplicate frame(s)!
Pos: 207.7s   4531f (99%) 230.55fps Trem:   0min 436mb  A-V:-0.083 [15871:1725]

1 duplicate frame(s)!
Pos: 208.2s   4541f (99%) 231.04fps Trem:   0min 437mb  A-V:-0.083 [15907:1725]

1 duplicate frame(s)!
Pos: 208.7s   4551f (99%) 231.51fps Trem:   0min 440mb  A-V:-0.083 [15961:1725]

1 duplicate frame(s)!
Pos: 209.1s   4561f (99%) 231.99fps Trem:   0min 441mb  A-V:-0.083 [15994:1725]

1 duplicate frame(s)!
Pos: 209.6s   4571f (99%) 232.49fps Trem:   0min 441mb  A-V:-0.083 [15968:1725]

1 duplicate frame(s)!
Pos: 210.0s   4581f (99%) 232.99fps Trem:   0min 442mb  A-V:-0.083 [15942:1725]

1 duplicate frame(s)!
Pos: 210.5s   4591f (99%) 233.50fps Trem:   0min 442mb  A-V:-0.083 [15916:1725]

1 duplicate frame(s)!
Pos: 211.0s   4601f (99%) 233.99fps Trem:   0min 442mb  A-V:-0.083 [15895:1725]

1 duplicate frame(s)!
Pos: 211.4s   4611f (100%) 232.54fps Trem:   0min 442mb  A-V:-0.083 [15869:1711]

1 duplicate frame(s)!
Pos: 211.9s   4621f (100%) 233.03fps Trem:   0min 442mb  A-V:-0.083 [15848:1711]

1 duplicate frame(s)!
Pos: 212.3s   4631f (100%) 233.54fps Trem:   0min 442mb  A-V:-0.083 [15822:1711]

1 duplicate frame(s)!
Pos: 212.8s   4641f (100%) 234.03fps Trem:   0min 442mb  A-V:-0.083 [15794:1711]

1 duplicate frame(s)!
Pos: 213.3s   4651f (100%) 234.53fps Trem:   0min 443mb  A-V:-0.083 [15775:1711]

1 duplicate frame(s)!
Pos: 213.7s   4661f (100%) 235.02fps Trem:   0min 443mb  A-V:-0.083 [15750:1711]

1 duplicate frame(s)!
Pos: 214.2s   4671f (100%) 235.53fps Trem:   0min 443mb  A-V:-0.083 [15724:1711]

1 duplicate frame(s)!
Pos: 214.6s   4681f (100%) 236.02fps Trem:   0min 443mb  A-V:-0.083 [15698:1711]

1 duplicate frame(s)!
Pos: 215.1s   4691f (100%) 236.52fps Trem:   0min 443mb  A-V:-0.083 [15671:1711]

1 duplicate frame(s)!
Pos: 215.5s   4701f (100%) 237.03fps Trem:   0min 444mb  A-V:-0.083 [15644:1711]

1 duplicate frame(s)!
Pos: 216.0s   4711f (100%) 237.52fps Trem:   0min 444mb  A-V:-0.083 [15630:1711]

1 duplicate frame(s)!
Pos: 216.5s   4721f (100%) 238.01fps Trem:   0min 444mb  A-V:-0.083 [15606:1711]

1 duplicate frame(s)!
Pos: 216.9s   4731f (100%) 238.52fps Trem:   0min 445mb  A-V:-0.083 [15582:1711]

1 duplicate frame(s)!
Pos: 217.4s   4741f (100%) 238.91fps Trem:   0min 445mb  A-V:-0.083 [15556:1711]

1 duplicate frame(s)!
Pos: 217.8s   4751f (100%) 239.42fps Trem:   0min 445mb  A-V:-0.083 [15532:1711]

1 duplicate frame(s)!
Pos: 218.3s   4761f (100%) 239.91fps Trem:   0min 445mb  A-V:-0.083 [15507:1711]

1 duplicate frame(s)!
Pos: 218.8s   4771f (100%) 240.41fps Trem:   0min 445mb  A-V:-0.083 [15481:1711]

1 duplicate frame(s)!
Pos: 219.2s   4781f (100%) 240.90fps Trem:   0min 446mb  A-V:-0.083 [15457:1711]

1 duplicate frame(s)!
Pos: 219.7s   4791f (100%) 241.41fps Trem:   0min 446mb  A-V:-0.083 [15432:1711]

1 duplicate frame(s)!
Pos: 220.1s   4801f (100%) 241.90fps Trem:   0min 446mb  A-V:-0.083 [15408:1711]

1 duplicate frame(s)!
Pos: 220.6s   4811f (100%) 242.39fps Trem:   0min 447mb  A-V:-0.083 [15408:1711]

1 duplicate frame(s)!
Pos: 221.1s   4821f (100%) 242.90fps Trem:   0min 447mb  A-V:-0.083 [15384:1711]

1 duplicate frame(s)!
Pos: 221.5s   4831f (100%) 243.39fps Trem:   0min 447mb  A-V:-0.083 [15362:1711]

1 duplicate frame(s)!
Pos: 221.6s   4833f (100%) 243.49fps Trem:   0min 447mb  A-V:-0.050 [15360:1711]
Too many subtitle lines
Pos: 222.0s   4841f (100%) 243.88fps Trem:   0min 448mb  A-V:-0.083 [15341:1711]

1 duplicate frame(s)!
Pos: 222.4s   4851f (100%) 244.38fps Trem:   0min 448mb  A-V:-0.083 [15324:1711]

1 duplicate frame(s)!
Pos: 222.9s   4861f (100%) 244.86fps Trem:   0min 448mb  A-V:-0.083 [15304:1711]

1 duplicate frame(s)!
Pos: 223.3s   4871f (100%) 245.35fps Trem:   0min 449mb  A-V:-0.083 [15286:1711]

1 duplicate frame(s)!
Pos: 223.8s   4881f (100%) 245.86fps Trem:   0min 449mb  A-V:-0.083 [15261:1711]

1 duplicate frame(s)!
Pos: 224.3s   4891f (100%) 246.35fps Trem:   0min 449mb  A-V:-0.083 [15245:1711]

1 duplicate frame(s)!
Pos: 224.7s   4901f (100%) 246.84fps Trem:   0min 449mb  A-V:-0.083 [15219:1711]

1 duplicate frame(s)!
Pos: 225.2s   4911f (100%) 247.34fps Trem:   0min 449mb  A-V:-0.083 [15190:1711]

1 duplicate frame(s)!
Pos: 225.6s   4921f (100%) 247.85fps Trem:   0min 449mb  A-V:-0.083 [15161:1711]

1 duplicate frame(s)!
Pos: 226.1s   4931f (100%) 248.34fps Trem:   0min 449mb  A-V:-0.083 [15130:1711]

1 duplicate frame(s)!
Pos: 226.5s   4940f (100%) 248.79fps Trem:   0min 449mb  A-V:-0.079 [15102:1711]
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream: 15100.104 kbit/s  (1887513 B/s)  size: 427634337 bytes  226.560 secs  4940 frames

Audio stream: 1711.878 kbit/s  (213984 B/s)  size: 44097977 bytes  206.080 secs
```

Also, when I tried playing the video, I got an error, although it *did* seem to play without any obvious errors (see screenshot [here]("http://www.pictureshack.us/images/52093_sceenshot2.png")).  By "undf", I assume it means "undefined".

---

### Post by shantiq on 2012-07-08
your command was wrong    look


> mencoder -ss 00:20:40 -endpos [COLOR="DarkRed"]00:22:25[/COLOR] -oac copy -ovc copy 'Episode 7.mkv' -o output.mkv



the second time has to be the length of the cut;    not the time when it stops


you need 


> mencoder -ss 00:20:40 -endpos [COLOR="DarkRed"]00:01:45[/COLOR] -oac copy -ovc copy 'Episode 7.mkv' -o output.mkv




try this see how it goes this time:KS


also    try vlc   mplayer   see which one it plays best in

ps subs can only be done this way if they are burnt in

---

### Post by Merrattic on 2012-07-08
ffmpeg has forked development now, hence the deprecated alert

Problem with your ffmpeg line is that you are re-encoding rather than copying, you need to add the copy parameters for video and audio (although this may introduce other issues including A/V sync!!). Something like: ```
ffmpeg -i input.mkv -ss 00:01:00 -t 100 -vcodec copy -acodec copy output.mkv
```

---

### Post by shantiq on 2012-07-08
this here will retain the subtitle but it is involved    up to you



1 First we install mkvmerge to extract the srt file you wish to have
2 Then we burn it in using mencoder
3 Then run the cutting command





to install mkvmerge
```
sudo apt-get install mkvtoolnix

```



First, use mkvmerge to list the MKV file&#8217;s contents:

```
mkvmerge -i MovieFile.mkv

```You&#8217;ll see a listing similar to this:

File 'MovieFile.mkv': container: Matroska
Track ID 1: subtitles (S_TEXT/***)
Track ID 2: audio (A_MPEG/L3)
Track ID 3: video (V_MPEG4/ISO/AVC)


Next, use mkvextract to extract certain tracks / attachments based on the output from the above command:

> mkvextract tracks MovieFile.mkv 1:thesubtitles.srt
  2:theaudio.mp3 3:thevideo.mp4

of course only use the number you want here
  

  
    
      To then burn in your extracted srt file into your video
      [this takes a while--maybe an hour]  
  
>  mencoder -sub file.srt -subcp iso-8857-9 -ovc xvid -xvidencopts bitrate=1419 -oac copy -o newfilewithsub.mkv originalfile.mkv

  
  
  and finally
  
  
> mencoder -ss 00:20:40 -endpos 00:01:45 -oac copy -ovc copy 'Episode 7.mkv' -o output.mkv



This will give you what you asked for

I do not know any other route that is easier for this [ subtitle adds difficulty]:KS

---

### Post by Stonecold1995 on 2012-07-08
> **shantiq said:**
> try this see how it goes this time:KS


also    try vlc   mplayer   see which one it plays best in

ps subs can only be done this way if they are burnt in

I just tried that.  The timing was correct, however there's still no audio when I play it in VLC (and I still get the "undf" error).  When I play it through SMPlayer, it plays and the audio works, however SMPlayer seems not to know the length of the video.  The progress bar never moves, and it thinks it's playing at a much higher rate than it actually is ([screenshot]("http://www.pictureshack.us/images/974_sceenshot4.png")).  You can see in the screenshot that it thinks I've been playing the video for almost 480 hours!  The progress bar hasn't moved an inch, yet the scene in the screenshot occurs near the end of the clip.  The same scene on VLC ([screenshot]("http://www.pictureshack.us/images/63224_sceenshot3.png")) shows the play time correctly (1:38) but has no sound and has the "undf" popup.

How do I get it so that VLC is able to play the audio and SMPlayer is able to keep time correctly?

---

### Post by FakeOutdoorsman on 2012-07-10
> **Merrattic said:**
> ffmpeg has forked development now, hence the deprecated alert

Problem with your ffmpeg line is that you are re-encoding rather than copying, you need to add the copy parameters for video and audio (although this may introduce other issues including A/V sync!!). Something like: ```
ffmpeg -i input.mkv -ss 00:01:00 -t 100 -vcodec copy -acodec copy output.mkv
```

Additionally, *-scodec copy* and maybe even *-dcodec copy* to preserve the subtitles and possibly the font files. Or just use *-c copy* to copy all inputs if your ffmpeg is new enough. I don't use the version from the repo, so I'm unsure if it supports *-c copy*. See [Compile FFmpeg on Ubuntu](http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide) if you want to try something newer than what is offered in the repository.

---

### Post by shantiq on 2012-07-11
hi there fake

well tried the -c copy with the repo version   and it is not recognized but this here worked a treat   [   and copies the default sub]    and way quicker than my convoluted offering

so for the asker this should swing it



> 
ffmpeg -i input.mkv -ss 00:20:40 -t 105 -acodec copy -vcodec copy -scodec copy -dcodec copy output.mkv

---

### Post by Stonecold1995 on 2012-07-11
> **shantiq said:**
> hi there fake

well tried the -c copy with the repo version   and it is not recognized but this here worked a treat   [   and copies the default sub]    and way quicker than my convoluted offering

so for the asker this should swing it

"Could not find input stream matching output stream #0.3"
```
alex@kubuntu:~/Videos/Mahou Shoujo Madoka Magica$ ffmpeg -i 'Episode 7.mkv' -ss 00:20:40 -t 105 -acodec copy -vcodec copy -scodec copy -dcodec copy output.mkv
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[matroska,webm @ 0x1ec79c0] max_analyze_duration reached
[matroska,webm @ 0x1ec79c0] Estimating duration from bitrate, this may be inaccurate
Input #0, matroska,webm, from 'Episode 7.mkv':
  Metadata:
    title           : Mahou Shoujo Madoka Magika Episode 07 - Can You Face Your True Feelings
  Duration: 00:24:12.09, start: 0.000000, bitrate: N/A
    Chapter #0.0: start 0.000000, end 158.116000
    Metadata:
      title           : Prologue
    Chapter #0.1: start 158.116000, end 248.081000
    Metadata:
      title           : Opening
    Chapter #0.2: start 248.081000, end 727.018000
    Metadata:
      title           : Part A
    Chapter #0.3: start 727.018000, end 1346.011000
    Metadata:
      title           : Part B
    Chapter #0.4: start 1346.011000, end 1436.060000
    Metadata:
      title           : Ending
    Chapter #0.5: start 1436.060000, end 1452.095000
    Metadata:
      title           : Preview
    Stream #0.0(jpn): Video: h264 (High 10), yuv420p10le, 1920x1080 [PAR 1:1 DAR 16:9], 23.98 fps, 23.98 tbr, 1k tbn, 47.95 tbc (default)
    Metadata:
      title           : Video track
    Stream #0.1(jpn): Audio: flac, 48000 Hz, 2 channels, s32 (default)
    Metadata:
      title           : Audio track
    Stream #0.2(jpn): Audio: aac, 48000 Hz, stereo, s16
    Metadata:
      title           : Audio track - Commentary
    Stream #0.3(eng): Subtitle: *** (default)
    Metadata:
      title           : Subtitle track
    Stream #0.4(eng): Subtitle: ***
    Metadata:
      title           : Subtitle track - Commentary
    Stream #0.5(eng): Subtitle: ***
    Metadata:
      title           : Subtitle track - Colorless
    Stream #0.6: Attachment: [0][0][0][0] / 0x0000
    Metadata:
      filename        : Doradani_Rg_Bold.ttf
      mimetype        : application/x-truetype-font
    Stream #0.7: Attachment: [0][0][0][0] / 0x0000
    Metadata:
      filename        : Doradani Rg Bold Italic.ttf
      mimetype        : application/x-truetype-font
    Stream #0.8: Attachment: [0][0][0][0] / 0x0000
    Metadata:
      filename        : FOT-GrecoStd-M-ED3-8v2.otf
      mimetype        : application/x-truetype-font
    Stream #0.9: Attachment: [0][0][0][0] / 0x0000
    Metadata:
      filename        : PRISTINA-ED3-8v2.TTF
      mimetype        : application/x-truetype-font
    Stream #0.10: Attachment: [0][0][0][0] / 0x0000
    Metadata:
      filename        : love-OPv3.ttf
      mimetype        : application/x-truetype-font
    Stream #0.11: Attachment: [0][0][0][0] / 0x0000
    Metadata:
      filename        : angelina.ttf
      mimetype        : application/x-truetype-font
    Stream #0.12: Attachment: [0][0][0][0] / 0x0000
    Metadata:
      filename        : ARIALUNI-ep07.TTF
      mimetype        : application/x-truetype-font
    Stream #0.13: Attachment: [0][0][0][0] / 0x0000
    Metadata:
      filename        : mona-ep07.ttf
      mimetype        : application/x-truetype-font
    Stream #0.14: Attachment: [0][0][0][0] / 0x0000
    Metadata:
      filename        : tahoma-ep07.ttf
      mimetype        : application/x-truetype-font
Output #0, matroska, to 'output.mkv':
    Stream #0.0: Video: [0][0][0][0] / 0x0000, q=2-31, 200 kb/s, 90k tbn
    Stream #0.1: Audio: [0][0][0][0] / 0x0000, 0 channels, 200 kb/s
    Stream #0.2: Subtitle: [0][0][0][0] / 0x0000, 200 kb/s
    Stream #0.3: Data: [0][0][0][0] / 0x0000, 200 kb/s
Could not find input stream matching output stream #0.3
```

---

### Post by Merrattic on 2012-07-11
Look like we are close, but you may need to do some stream mapping. I am rubbish at doing this or remembering how it works :(

---

### Post by SeijiSensei on 2012-07-11
Might I humbly suggest that advertising you are using a fansubbed episode from *Madoka* on a public site isn't perhaps the best thing to do?  You should obfuscate the title in situations like this.

---

### Post by Stonecold1995 on 2012-07-11
> **SeijiSensei said:**
> Might I humbly suggest that advertising you are using a fansubbed episode from *Madoka* on a public site isn't perhaps the best thing to do?  You should obfuscate the title in situations like this.
I actually had no idea that was fansubbed.  I thought the subs were official. :confused: Alright, maybe if I rename it "Game of Thrones" next time it'll draw a little less attention. ;)

---

### Post by houseworkshy on 2012-07-11
The easy way would be to install kdenlive from the repros and do it through a gui editor.  Cinelerra which isn't in the repros but is the best I've seen,  can be got here [http://cinelerra.org/getting_cinelerra.php](http://cinelerra.org/getting_cinelerra.php).  Both are nonlinear so the original material is safe.  Avidimux is also ok as is kino, though one usually has to convert to use it.

---

