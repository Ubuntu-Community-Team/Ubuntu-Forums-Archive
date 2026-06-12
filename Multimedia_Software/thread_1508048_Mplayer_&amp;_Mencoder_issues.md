---
title: "Mplayer &amp; Mencoder issues"
date: 2010-06-12
forum: Multimedia Software
---

### Post by MooPi on 2010-06-12
I bought the DVD Wall-E some time ago and wanted to rip to hard drive. Problems started with playback, Mplayer would shut down after a couple of seconds. I remedied the problem by adjusting the start by 4 seconds. Played great but now the same title will not record via MEncoder. I get no sound and the video is short maybe just first chapter. I previously thought that mplayer would not play Disney movies. I've got past that issue and now MEncoder is a problem. I have always understood that anything that Mplayer could play MEncoder could record. Anyone proficient in either.This is my script for mencoder:
```
#!/bin/bash
# remove conflicting files
rm -f divx2pass.log frameno.avi

# rip audio track (bitrate: 128, gain: 0)
nice -n 3 mencoder -oac mp3lame -lameopts mode=2:cbr:br=128:vol=0 \
 -ovc frameno -o frameno.avi -ss 4 dvd://30

# video track (pass: 1, bitrate: 2000)
nice -n 3 mencoder -sws 2 -oac copy -ovc lavc \
 -lavcopts vcodec=mpeg4:vbitrate=2000:vhq:vpass=1 \
 -ffourcc XVID  -ss 4 dvd://30 -o /dev/null

# video track (pass: 2, bitrate: 2000)
nice -n 3 mencoder -sws 2 -oac copy -ovc lavc \
 -lavcopts vcodec=mpeg4:vbitrate=2000:vhq:vpass=2 \
 -ffourcc XVID  -ss 4 dvd://30 -o "Wall-E.avi"

# done
```
Mplayer command to play : ```
mplayer -ss 4 dvd://30
```
Now the first parts of movie log:
```
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team

Playing dvd://30.
There are 99 titles on this DVD.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
audio stream: 1 format: ac3 (stereo) language: en aid: 129.
audio stream: 2 format: ac3 (stereo) language: en aid: 130.
number of audio channels on disk: 3.
subtitle ( sid ): 1 language: en
subtitle ( sid ): 3 language: en
number of subtitles on disk: 2
MPEG-PS file format detected.
MPEG: No audio stream found -> no sound.
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  9800.0 kbps (1225.0 kbyte/s)
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 854x480 Planar YV12 
V:   0.0   1/  1 ??% ??% ??,?% 0 0 [J
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
```

---

### Post by MooPi on 2010-06-18
Okay a slight update. I changed the way I ripped from a direct ripping to mplayer streamdump. I then encode the dump.vob file to avi. Problem still exits with the first chapter and the transition to the 2nd chapter. I dumped from the 2nd chapter to the end of the DVD. The first chapter eludes me thus far. I have the first chapter minus sound. UGHHHH. This is my dump command : ```
mplayer -ss 4 dvd://30 -chapter 2-33 streamdump -dumpfile movie.vob
```Any help to work past the transition from 1st to 2nd chapter would be greatly appreciated.

---

### Post by sacani on 2013-01-06
[http://threebrothers.org/brendan/blog/encoding-ipad-video-from-linux/](http://threebrothers.org/brendan/blog/encoding-ipad-video-from-linux/)



$ dvdbackup -I
##### Output indicate that main title is 3
$dvdbackup -T 3
##### 
....
####
$for x in *.VOB; do cat $x >> walle.vob; done

---

### Post by overdrank on 2013-01-06
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

