---
title: "mencoder sync issues"
date: 2007-02-01
forum: Multimedia &amp; Video
---

### Post by pieroxy on 2007-02-01
I am trying to encode a bunch of videos with mencoder and am faced with the (almost) same issue every single time. mencoder complains that it has to duplicate / drop frames during the entire encoding process and in the resulting AVI the sound is either out of sync, or broken (will play for a few secs then will stop).

Once it was because ffmpeg couldn't detect the input framerate on an ASF file, so I forced the framerate with -fps, but still had to manually specify -mc 0 that time.

Another time it was because the 'oac copy' didn"t work. With '-oac mp3lame' it works fine. I still hasn't resolved this issue either.

This time I have an MPEG-TS file (MPEG2 1080i, interlaced 29.970fps and AC3 5.1) and no matter what I do, I still get the output below...

Any help? Is there a common way to solve these issues?

Here is my command-line (for pass2 for example):
mencoder -o "$2" -vf pp=lb -vf scale=1280:720 -ovc xvid -oac mp3lame "$1" -xvidencopts chroma_opt:vhq=4:bvhq=1:quant_type=mpeg:bitrate=2000****:****pass=2 -aspect 16:9 -mc 0 -fps 24000/1001

Here is the output:
__________________________________________________________________
MEncoder 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Sempron(tm) 2500+ (Family: 6, Model: 8, Stepping: 1)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0xbff65bbc
TS file format detected.
DEMUX OPEN, AUDIO_ID: -1, VIDEO_ID: -1, SUBTITLE_ID: -2,
PROBING UP TO 2000000, PROG: 0
VIDEO MPEG2(pid=17)AUDIO A52(pid=20) NO SUBS (yet)!  PROGRAM N. 1
Opened TS demuxer, audio: 2000(pid 20), video: 10000002(pid 17)...POS=3008, PROBE=2000000
VIDEO:  MPEG2  1920x1080  (aspect 3)  29.970 fps  80000.0 kbps (10000.0 kbyte/s)
[V] filefmt:29  fourcc:0x10000002  size:1920x1080  fps:29.97  ftime:=0.0334
Input fps will be interpreted as 23.98 instead.
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
AC3: 5.1 (3f+2r+lfe)  48000 Hz  384.0 kbit/s
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
xvid: using library version 1.1.0 (build xvid-1.1.0)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [scale w=1280 h=720]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 1920 x 1080 (preferred colorspace: Mpeg PES)
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
VDec: vo config request - 1920 x 1080 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.

SwScaler: BICUBIC scaler, from Planar YV12 to Planar YV12 using MMX2
videocodec: XviD (1280x720 fourcc=44495658 [XVID])
xvid: par=0/0 (vga11), displayed=1280x720, sampled=1280x720
xvid: 2Pass Rate Control -- 1st pass
Writing header...2f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
ODML: vprp aspect is 16:9.
Setting audio delay to 0.024s.
Writing header...
ODML: vprp aspect is 16:9.
Setting audio delay to 0.024s.

1 duplicate frame(s)!
Pos:   2.5s     62f ( 0%) 18.78fps Trem:   0min   0mb  A-V:0.000 [144:178]
1 duplicate frame(s)!
Pos:   2.7s     66f ( 0%) 18.53fps Trem:   0min   0mb  A-V:0.000 [177:179]
1 duplicate frame(s)!
Pos:   2.9s     70f ( 0%) 18.39fps Trem:   0min   0mb  A-V:0.000 [205:181]
1 duplicate frame(s)!
Pos:   3.1s     74f ( 0%) 18.35fps Trem:   0min   0mb  A-V:0.000 [235:182]
1 duplicate frame(s)!
Pos:   3.3s     78f ( 0%) 18.11fps Trem:   0min   0mb  A-V:0.000 [294:184]
1 duplicate frame(s)!
Pos:   3.5s     82f ( 0%) 17.98fps Trem:   0min   0mb  A-V:0.000 [329:185]
1 duplicate frame(s)!
Pos:   3.7s     86f ( 0%) 17.92fps Trem:   0min   0mb  A-V:0.000 [353:186]
1 duplicate frame(s)!
Pos:   3.9s     90f ( 0%) 17.74fps Trem:   0min   0mb  A-V:0.000 [409:187]
1 duplicate frame(s)!
Pos:   4.1s     94f ( 0%) 17.61fps Trem:   0min   0mb  A-V:0.000 [435:189]
1 duplicate frame(s)!
Pos:   4.3s     98f ( 0%) 17.60fps Trem:   0min   0mb  A-V:0.000 [459:190]
1 duplicate frame(s)!
Pos:   4.5s    102f ( 0%) 17.46fps Trem:   0min   0mb  A-V:0.000 [503:191]
1 duplicate frame(s)!
Pos:   4.8s    106f ( 0%) 17.38fps Trem:   0min   0mb  A-V:0.000 [527:191]
1 duplicate frame(s)!
Pos:   5.0s    110f ( 0%) 17.38fps Trem:   0min   0mb  A-V:0.000 [546:192]
1 duplicate frame(s)!
Pos:   5.2s    114f ( 0%) 17.26fps Trem:   0min   0mb  A-V:0.000 [592:193]
1 duplicate frame(s)!
Pos:   5.4s    118f ( 0%) 17.18fps Trem:   0min   0mb  A-V:0.000 [610:194]
1 duplicate frame(s)!
Pos:   5.5s    121f ( 0%) 17.15fps Trem:   0min   0mb  A-V:0.000 [634:194]

---

### Post by pseudonym on 2007-02-01
I only work with mpeg files (DVB > DVD), but I've found the 'harddup' option to be helpful here. From the mencoder manpage - ```
harddup
	
Only useful with MEncoder. If harddup is used when encoding, it will force duplicate frames to be encoded in the output. This uses slightly more space, but is necessary for output to MPEG files or if you plan to demux and remux the video stream after encoding. Should be placed at or near the end of the filter chain unless you have a good reason to do otherwise.
```

To use it, make your command line look like this - ```
.... -vf scale=1280:720,harddup ....
```

---

### Post by pieroxy on 2007-02-01
I'll try that, but the question remains: Why does it need to duplicate frames ?

---

### Post by pieroxy on 2007-02-18
Hi,

A quick reply to say that nothing I found works for me so far. So the issue is still opened. I basically investigated three distinct solutions: harddup, -mc 0 and -noskip but neither works (neither any combination of the three worked).

If anyone has any other idea, I'm buying ;-)

---

### Post by david_2001 on 2007-02-19
(Ignore me, I just posted the answer to the wrong question.)

---

### Post by david_2001 on 2007-02-20
> **pieroxy said:**
> I am trying to encode a bunch of videos with mencoder and am faced with the (almost) same issue every single time. mencoder complains that it has to duplicate / drop frames during the entire encoding process and in the resulting AVI the sound is either out of sync, or broken (will play for a few secs then will stop).

Once it was because ffmpeg couldn't detect the input framerate on an ASF file, so I forced the framerate with -fps, but still had to manually specify -mc 0 that time.

Another time it was because the 'oac copy' didn"t work. With '-oac mp3lame' it works fine. I still hasn't resolved this issue either.

This time I have an MPEG-TS file (MPEG2 1080i, interlaced 29.970fps and AC3 5.1) and no matter what I do, I still get the output below...

Any help? Is there a common way to solve these issues?

Here is my command-line (for pass2 for example):
mencoder -o "$2" -vf pp=lb -vf scale=1280:720 -ovc xvid -oac mp3lame "$1" -xvidencopts chroma_opt:vhq=4:bvhq=1:quant_type=mpeg:bitrate=2000****:****pass=2 -aspect 16:9 -mc 0 -fps 24000/1001


Back again.  Couple of questions:
[LIST=1]
[*]"-fps 24000/1001" does not give 29.97 fps, which is 30000/1001, so the input is being forced to be something it isn't.  Are you attempting framerate conversion?
[*]MPEG-TS streams are notorious for a/v sync problems when transcoding.  Did you try running the file through ProjectX first to fix transmission errors (I believe that ProjectX will work with NTSC 1080i recordings)?
[/LIST]

---

### Post by superm1 on 2007-02-21
> **david_2001 said:**
> Back again.  Couple of questions:[LIST=1]
[*]"-fps 24000/1001" does not give 29.97 fps, which is 30000/1001, so the input is being forced to be something it isn't.  Are you attempting framerate conversion?
[*]MPEG-TS streams are notorious for a/v sync problems when transcoding.  Did you try running the file through ProjectX first to fix transmission errors (I believe that ProjectX will work with NTSC 1080i recordings)?[/LIST]
I'm encountering similar problems with Mpeg-ts streams.  I've ran them through the mythtv mpeg2-mpeg2 transcode to clean them um, but still get pretty nasty skip at the end.
This is the encoding script i'm using (FROM myth mailing list):
```
#!/bin/sh
nice -n 18 mencoder \
-vf harddup \
-ovc copy \
-oac copy \
-of rawaudio \
-o "${2}.ac3" \
"${1}" && \
nice -n 18 mencoder \
-vf pullup,softskip,${3},scale=1360:768,harddup \
-ofps 24000/1001 \
-ovc x264 \
-x264encopts \
bitrate=2000:pass=1:turbo=2:keyint=240:bframes=3:direct_pred=3 
\
-oac copy \
-o /dev/null \
"${1}" && \
nice -n 18 mencoder \
-vf pullup,softskip,${3},scale=1360:768,harddup \
-ofps 24000/1001 \
-ovc x264 \
-x264encopts \
bitrate=2000:pass=2:turbo=2:keyint=240:bframes=3:direct_pred=3 \
-oac copy \
-of rawvideo \
-o "${2}.264" \
"${1}" && \
nice -n 18 MP4Box "${2}.mp4" -fps 23.976 -add "${2}.264" && \
nice -n 18 mkvmerge -o "${2}.mkv" "${2}.mp4" "${2}.ac3" && \
rm "${2}.264" "${2}.ac3" "${2}.mp4" 

```

---

### Post by david_2001 on 2007-02-21
> I'm encountering similar problems with Mpeg-ts streams. I've ran them through the mythtv mpeg2-mpeg2 transcode to clean them um, but still get pretty nasty skip at the end.
This is the encoding script i'm using (FROM myth mailing list):
Hmm.  Are we dealing with a TV recording?[LIST=1]
[*]A "nasty skip at the end" is presumably either a transmission error that's gone uncorrected or a transmission error that's been corrected by deleting some frames.
[*]That encoding script is intended to transcode a "difficult" progressive/telecine stream that has been ripped from a DVD.  It's unlikely to be much use at transcoding a transport stream that's been captured from broadcast TV, if that's what you've got.  (I've got some NTSC DVDs that I could test it with but no suitable TV recordings because I live in a PAL region.)
[*]Do you need to scale the video?  There's no need to rescale to, for example, the maximum resolution your television can display.  All scaling does during transcoding is reduce picture quality.
[/LIST]

---

### Post by superm1 on 2007-02-21
> **david_2001 said:**
> Hmm.  Are we dealing with a TV recording?[LIST=1]
[*]A "nasty skip at the end" is presumably either a transmission error that's gone uncorrected or a transmission error that's been corrected by deleting some frames.
[*]That encoding script is intended to transcode a "difficult" progressive/telecine stream that has been ripped from a DVD.  It's unlikely to be much use at transcoding a transport stream that's been captured from broadcast TV, if that's what you've got.  (I've got some NTSC DVDs that I could test it with but no suitable TV recordings because I live in a PAL region.)
[*]Do you need to scale the video?  There's no need to rescale to, for example, the maximum resolution your television can display.  All scaling does during transcoding is reduce picture quality.[/LIST]
I should have clarified better about my content and usage. 

These are from TV recordings OTA in a transport stream.  They are cleaned similar to the projectX method by mythtv's mpeg2-mpeg2 transcoder.  The end result is a fairly large mpeg2 file with av synced up but without any transmission errors.

Nasty skip at the end is a really bad description of the problem.  The A/V is progressively more and more out of sync by the end of the recording.  For a 42 min recording, it is almost 1/2 second off by the end.

The video is broadcast in either 1920x1080i or 1280x720p (depending on the TV network).  My TV (the only place I ever intend to watch them) has a native resolution of 1360x768.  I figured if I targeted that, I wouldn't have to worry about any software scaling happening during playback.  The machine already struggles enough to playback h264, I assume having to scale it wouldn't be much better.  I for sure can't play h264 at 1920x540p or 1920x1080p on the TV with h264.  When I experimented with 720p, it was acceptable.

The reason I'm using such a complex script was my understanding that AC3 needs to be separated from the video and then remuxed when working with a transport stream.

The problem appears to be that there are several frames that are just skipped.  I see hundreds of messages that say "Skipped Frame" during the encoding process.

---

### Post by david_2001 on 2007-02-22
Mencoder will inform the user about incorrect command line parameters but unfortunately doesn't provide an opinion on whether the chosen parameters will give the desired end result ;).  Getting a/v sync is hit or miss, too - you've just got to get everything right and running sweetly (it's not difficult to find adverse comments about the way mencoder does a/v synchronisation).

Anyway, that script is doing framerate conversion, from broadcast NTSC (30000/1001) to 24000/1001, so frames will have to be dropped/skipped in order to get there.  Secondly, it's really not a good idea to scale an interlaced stream, even though mencoder will do it without complaining.  Thirdly, due to living in a PAL region, I've absolutely no experience of working with NTSC recordings, and due to living in the UK and being a cheapskate, no HDTV experience either.  I just record and burn the local free-to-air 576i digital transmissions to either SVCD or DVD with minimal rework - just ProjectX followed by a little trimming and cutting, and recoding for SVCD.  For DVD I only need to recode material from certain channels that broadcast with extraordinarily long GOP lengths that are way, way outside the PAL DVD standard of 12.

Did you ever visit [www.doom9.org](www.doom9.org)?  There's a considerable amount of material there, including this [COLOR="SandyBrown"][thread]("http://forum.doom9.org/showthread.php?p=951020")[/COLOR], which may take your interest.  It includes a script that does more or less the same thing as the one you are trying but in a much more sophisticated way (including deinterlacing before scaling) and may be worth a try.

---

### Post by superm1 on 2007-02-22
> **david_2001 said:**
> Mencoder will inform the user about incorrect command line parameters but unfortunately doesn't provide an opinion on whether the chosen parameters will give the desired end result ;).  Getting a/v sync is hit or miss, too - you've just got to get everything right and running sweetly (it's not difficult to find adverse comments about the way mencoder does a/v synchronisation).

Anyway, that script is doing framerate conversion, from broadcast NTSC (30000/1001) to 24000/1001, so frames will have to be dropped/skipped in order to get there.  Secondly, it's really not a good idea to scale an interlaced stream, even though mencoder will do it without complaining.  Thirdly, due to living in a PAL region, I've absolutely no experience of working with NTSC recordings, and due to living in the UK and being a cheapskate, no HDTV experience either.  I just record and burn the local free-to-air 576i digital transmissions to either SVCD or DVD with minimal rework - just ProjectX followed by a little trimming and cutting, and recoding for SVCD.  For DVD I only need to recode material from certain channels that broadcast material with extraordinarily long GOP lengths that are way, way outside the PAL DVD standard of 12.

Did you ever visit [www.doom9.org]("http://www.doom9.org")?  There's a considerable amount of material there, including this [COLOR=SandyBrown][thread]("http://forum.doom9.org/showthread.php?p=951020")[/COLOR], which may take your interest.  It includes a script that does more or less the same thing as the one you are trying but in a much more sophisticated way (including deinterlacing before scaling) and may be worth a try.
Thanks a bunch for the info.  Its a shame everything is so hit and miss with mencoder, but I'm sure this will pay off once that sweet spot is found and I can do the same thing for everything HD I record.  It didn't even click to me that a framerate change would cause dropped frames, but that is fairly logical now.  

I haven't visited much at doom9, I was always under the impression the people there were more about windows encoding techniques.

---

