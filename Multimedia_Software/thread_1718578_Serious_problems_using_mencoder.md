---
title: "Serious problems using mencoder"
date: 2011-03-31
forum: Multimedia Software
---

### Post by khelben1979 on 2011-03-31
Hello!

I have had serious problems making video clips using mencoder (it's part of the mplayer package) software and after many, many hours I'm asking here for help:

I use this from the command line:
mencoder -oac pcm -ovc lavc -vf rotate=1 mov00002.3gp -o potatoes.avi

and the result is good when it comes both video and audio + the fact that the video clip gets rotated the correct way, but... the speed of the video clip is maybe 10 times faster than what it should be and I have tried everything I can think of.

I have managed to solve this issue using ffmpeg after first using the mencoder software, but I don't remember how I did it... so maybe I can just use mencoder with the correct parameters instead, don't know yet.

So is there an Mencoder specialist somewhere on this Ubuntu forum? :)

This is some information from the original video clip in 3gp format, if it helps:
> bear@81-224-174-40-o1123:~/PICS_MOBILE/FOOD$ mplayer mov00002.3gp
MPlayer dev-SVN-r26940
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mov00002.3gp.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [s263]  176x144  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh263] vfm: ffmpeg (FFmpeg H.263+ decoder)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 8000 Hz, 1 ch, s16le, 0.0 kbit/0.00% (ratio: 0->16000)
Selected audio codec: [ffamrnb] afm: ffmpeg (AMR Narrowband)
==========================================================================
AO: [alsa] 8000Hz 1ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 176 x 144 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 176x144 => 192x144 Planar YV12 
[swscaler @ 0x8790ed8]using unscaled yuv420p -> rgb32 special converter
A:   4.2 V:   4.2 A-V:  0.000 ct:  0.001   0/  0  2%  1%  0.5% 1 0 
Exiting... (Quit)

---

### Post by SeijiSensei on 2011-03-31
> VIDEO: [s263] 176x144 24bpp **29.970 fps** 0.0 kbps ( 0.0 kbyte/s)


Try adding "-ofps 30000/1001" to force the output to run at ~30 frames per second like the source material.

---

### Post by khelben1979 on 2011-03-31
Is it ffmpeg or mencoder which should use the -ofps parameter? I tried with mencoder, but no luck!

---

### Post by FakeOutdoorsman on 2011-03-31
You could try using FFmpeg:
```
ffmpeg -i input -vf transpose=1 -acodec copy [output options] output
```
You will probably need to compile FFmpeg to get access to the filters:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by SeijiSensei on 2011-03-31
Yes, that's a mencoder option.  Please run the command

```
mplayer -identify -frames 0 /path/to/potatoes.avi | grep ID
```

and do the same for the source file, then post both sets of results so we can compare them.

While you're at it, what does "mencoder -ovc help" and "mencoder -oac help" show?  In the past when I put things into AVI containers, I used the XviD codec like this:

```
mencoder -o output.avi -oac mp3lame -ovc xvid -xvidencopts pass=1 /path/to/source.file
```

I don't know what codecs ship with mencoder by default in Ubuntu. I usually build it and mplayer from source.

---

### Post by khelben1979 on 2011-03-31
When doing  ```
mplayer -identify -frames 0 /path/to/potatoes.avi | grep ID
```  I get:

> bear@81-224-174-40-o1123:~/PICS_MOBILE/FOOD$ mplayer -identify -frames 0 /home/bear/PICS_MOBILE/FOOD/potatoes.avi | grep ID
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
ID_VIDEO_ID=0
ID_AUDIO_ID=1
VIDEO:  [FMP4]  144x176  24bpp  30.000 fps  623.6 kbps (76.1 kbyte/s)
ID_CLIP_INFO_NAME0=Software
ID_CLIP_INFO_VALUE0=MEncoder dev-SVN-r26940
ID_CLIP_INFO_N=1
ID_FILENAME=/home/bear/PICS_MOBILE/FOOD/potatoes.avi
ID_DEMUXER=avi
ID_VIDEO_FORMAT=FMP4
ID_VIDEO_BITRATE=623608
ID_VIDEO_WIDTH=144
ID_VIDEO_HEIGHT=176
ID_VIDEO_FPS=30.000
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=1
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_LENGTH=10.33
ID_SEEKABLE=1
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
ID_VIDEO_CODEC=ffodivx
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=8000
ID_AUDIO_NCH=1
ID_AUDIO_CODEC=pcm
bear@81-224-174-40-o1123:~/PICS_MOBILE/FOOD$ 

And when I go for the source file by using  ```
mplayer -identify -frames 0 /path/to/potatoes.avi | grep ID
```  it looks like this:
> bear@81-224-174-40-o1123:~/PICS_MOBILE/FOOD$ mplayer -identify -frames 0 /home/bear/PICS_MOBILE/FOOD/mov00002.3gp | grep ID
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
ID_VIDEO_ID=0
ID_AUDIO_ID=1
VIDEO:  [s263]  176x144  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
ID_FILENAME=/home/bear/PICS_MOBILE/FOOD/mov00002.3gp
ID_DEMUXER=lavfpref
ID_VIDEO_FORMAT=s263
ID_VIDEO_BITRATE=0
ID_VIDEO_WIDTH=176
ID_VIDEO_HEIGHT=144
ID_VIDEO_FPS=29.970
ID_VIDEO_ASPECT=1.3333
ID_AUDIO_FORMAT=samr
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=8000
ID_AUDIO_NCH=1
ID_LENGTH=46.20
ID_SEEKABLE=1
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
ID_VIDEO_CODEC=ffh263
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=8000
ID_AUDIO_NCH=1
ID_AUDIO_CODEC=ffamrnb


So if I can limit the fps on the clip to 30 fps, then problem will be solved. I got no solution to this yet. Sleep time for me here in Sweden, back here at Ubuntu.org tomorrow. :)

---

### Post by khelben1979 on 2011-04-01
More information from what was suggested:
> bear@81-224-174-40-o1123:~$ mencoder -ovc help
MEncoder dev-SVN-r26940 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Available codecs:
   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   nuv      - nuppel video
   lavc     - libavcodec codecs - best quality!
   vfw      - VfW DLLs, read DOCS/HTML/en/encoding-guide.html.
   qtvideo  - QuickTime DLLs, currently only SVQ1/3 are supported.
   libdv    - DV encoding with libdv v0.9.5
   xvid     - XviD encoding
   x264     - H.264 encoding

bear@81-224-174-40-o1123:~$ mencoder -oac help
MEncoder dev-SVN-r26940 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Available codecs:
   copy     - frame copy, without re-encoding (useful for AC3)
   pcm      - uncompressed PCM audio
   mp3lame  - cbr/abr/vbr MP3 using libmp3lame
   lavc     - FFmpeg audio encoder (MP2, AC3, ...)
   twolame  - Twolame MP2 audio encoder
   faac     - FAAC AAC audio encoder

This issue is still unresolved! Thanks for any additional help!

---

### Post by khelben1979 on 2011-04-02
Bump!

---

### Post by khelben1979 on 2011-04-03
Bump!

---

### Post by FakeOutdoorsman on 2011-04-03
You have no interest in trying FFmpeg instead?

---

### Post by SeijiSensei on 2011-04-03
Did you try encoding with XviD and mp3lame?  You have the necessary codecs.

---

### Post by khelben1979 on 2011-04-04
```
bear@81-224-174-40-o1123:~$ mencoder -o potatoes2.avi -oac mp3lame -ovc xvid -xvidencopts pass=1 /home/bear/PICS_MOBILE/FOOD/mov00002.3gp
```
> MEncoder dev-SVN-r26940 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0xbb7d1
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [s263]  176x144  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:44  fourcc:0x33363273  size:176x144  fps:29.970  ftime:=0.0334
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 8000 Hz, 1 ch, s16le, 0.0 kbit/0.00% (ratio: 0->16000)
Selected audio codec: [ffamrnb] afm: ffmpeg (AMR Narrowband)
==========================================================================
xvid: using library version 1.1.3 (build xvid-1.1.3)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh263] vfm: ffmpeg (FFmpeg H.263+ decoder)
==========================================================================
MP3 audio selected.
VDec: vo config request - 176 x 144 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
videocodec: XviD (176x144 fourcc=44495658 [XVID])
xvid: par=0/0 (vga11), displayed=192x144, sampled=176x144
xvid: 2Pass Rate Control -- 1st pass
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.
Writing header...
ODML: vprp aspect is 4:3.
Setting audio delay to 0.000s.
Writing header...
ODML: vprp aspect is 4:3.
Setting audio delay to 0.000s.
Pos:   0.7s     22f ( 8%)  0.00fps Trem:   0min   0mb  A-V:0.070 [0:51]
Skipping frame!
Pos:   1.0s     32f (12%)  0.00fps Trem:   0min   0mb  A-V:0.070 [0:51]
Skipping frame!
Pos:   1.3s     42f (12%)  0.00fps Trem:   0min   0mb  A-V:0.070 [620:52]
Skipping frame!
Pos:   1.6s     52f (16%)  0.00fps Trem:   0min   0mb  A-V:0.070 [616:52]
Skipping frame!
Pos:   1.9s     62f (20%)  0.00fps Trem:   0min   0mb  A-V:0.070 [607:53]
Skipping frame!
Pos:   2.2s     72f (24%)  0.00fps Trem:   0min   0mb  A-V:0.070 [598:52]
Skipping frame!
Pos:   2.5s     82f (24%)  0.00fps Trem:   0min   0mb  A-V:0.070 [599:53]
Skipping frame!
Pos:   2.8s     92f (29%)  0.00fps Trem:   0min   0mb  A-V:0.070 [609:53]
Skipping frame!
Pos:   3.1s    102f (33%)  0.00fps Trem:   0min   0mb  A-V:0.070 [606:53]
Skipping frame!
Pos:   3.4s    112f (33%)  0.00fps Trem:   0min   0mb  A-V:0.070 [603:53]
Skipping frame!
Pos:   3.7s    122f (37%)  0.00fps Trem:   0min   0mb  A-V:0.070 [597:53]
Skipping frame!
Pos:   4.0s    132f (41%)  0.00fps Trem:   0min   0mb  A-V:0.070 [585:54]
Skipping frame!
Pos:   4.3s    142f (41%)  0.00fps Trem:   0min   0mb  A-V:0.070 [572:53]
Skipping frame!
Pos:   4.6s    152f (46%)  0.00fps Trem:   0min   0mb  A-V:0.070 [564:53]
Skipping frame!
Pos:   4.9s    162f (50%)  0.00fps Trem:   0min   0mb  A-V:0.070 [571:54]
Skipping frame!
Pos:   5.2s    172f (50%)  0.00fps Trem:   0min   0mb  A-V:0.070 [570:54]
Skipping frame!
Pos:   5.5s    182f (54%)  0.00fps Trem:   0min   0mb  A-V:0.070 [576:54]
Skipping frame!
Pos:   5.8s    192f (58%)  0.00fps Trem:   0min   0mb  A-V:0.070 [578:54]
Skipping frame!
Pos:   6.1s    202f (62%)  0.00fps Trem:   0min   0mb  A-V:0.070 [579:54]
Skipping frame!
Pos:   6.4s    212f (62%)  0.00fps Trem:   0min   0mb  A-V:0.070 [585:54]
Skipping frame!
Pos:   6.7s    222f (67%)  0.00fps Trem:   0min   0mb  A-V:0.070 [591:54]
Skipping frame!
Pos:   7.0s    232f (71%)  0.00fps Trem:   0min   0mb  A-V:0.070 [592:54]
Skipping frame!
Pos:   7.3s    242f (71%)  0.00fps Trem:   0min   0mb  A-V:0.070 [591:54]
Skipping frame!
Pos:   7.6s    252f (75%)  0.00fps Trem:   0min   0mb  A-V:0.070 [589:54]
Skipping frame!
Pos:   7.9s    262f (79%)  0.00fps Trem:   0min   0mb  A-V:0.070 [588:54]
Skipping frame!
Pos:   8.2s    272f (79%)  0.00fps Trem:   0min   0mb  A-V:0.070 [588:54]
Skipping frame!
Pos:   8.5s    282f (84%)  0.00fps Trem:   0min   0mb  A-V:0.070 [586:54]
Skipping frame!
Pos:   8.8s    292f (88%) 287.12fps Trem:   0min   0mb  A-V:0.070 [585:54]
Skipping frame!
Pos:   9.1s    302f (92%) 289.55fps Trem:   0min   0mb  A-V:0.070 [584:54]
Skipping frame!
Pos:   9.4s    312f (92%) 291.59fps Trem:   0min   0mb  A-V:0.070 [582:54]
Skipping frame!
Pos:   9.7s    322f (96%) 294.06fps Trem:   0min   0mb  A-V:0.070 [577:54]
Skipping frame!
Pos:  10.0s    332f (96%) 296.69fps Trem:   0min   0mb  A-V:0.070 [572:54]
Skipping frame!
Pos:  10.3s    342f (100%) 298.69fps Trem:   0min   0mb  A-V:0.070 [574:54]
Skipping frame!
Pos:  10.3s    343f (100%) 299.30fps Trem:   0min   0mb  A-V:0.040 [574:54]
Flushing video frames.
Writing index...
Writing header...
ODML: vprp aspect is 4:3.
Setting audio delay to 0.000s.

Video stream:  574.524 kbit/s  (71815 B/s)  size: 742836 bytes  10.344 secs  343 frames

Audio stream:   54.507 kbit/s  (6813 B/s)  size: 73584 bytes  10.800 secs

Can you describe for me how I should do this with ffmpeg? My version of ffmpeg cannot rotate video clips, that's why I must use mencoder first and I simply don't remember how I did it with ffmpeg afterwards. :( Google searches didn't help either, no luck!

---

### Post by khelben1979 on 2011-04-05
Bump!

---

### Post by khelben1979 on 2011-04-06
Bump!

---

### Post by SeijiSensei on 2011-04-06
What was wrong with XviD-encoded file?  Did it not play correctly either?

Those skipped frames are typically duplicates.  I got errors like that from time to time depending on the source material.  The resulting AVI usually played fine regardless.

I really have nothing else to offer on this subject.  I've never seen a 3gp file in my life.  Most everything I've converted was in common containers like AVI, MP4, or MKV, and the codecs I've used are typically XviD or H.264.

---

### Post by khelben1979 on 2011-04-07
The 3gp file format is used in both Nokia and Sony Ericsson mobile phones, are you sure you've never seen it? I've found a temporary solution: letting the mobile camera be in the correct position from the beginning and just sending over the 3gp file.

I will let this thread be at peace now until someone decides to pick it up for further suggestions.

---

### Post by kthardin on 2011-04-08
Had a similar problem as noted in this thread which garnered no responses:

[http://ubuntuforums.org/showthread.php?t=1722681](http://ubuntuforums.org/showthread.php?t=1722681)

Tried this after a spectacular failure with AVISynth as detailed on this thread:

[http://ubuntuforums.org/showthread.php?t=1721837](http://ubuntuforums.org/showthread.php?t=1721837)

So I tried ffmpeg; which works.  Now I require further functionality with video filters (overlays and transitions), which were not included in ubuntu's ffmpeg build.  Running the video back through Mencoder with its filters tends to result in video that no longer plays.  I'm extremely reluctant to custom build ffmpeg as I tend to loose track of things when I do this.  Is there a package out there, not from the debian multimedia repository, that has the video filters already enabled?

Also, just as an aside, how would I go about causing audio to fade in and out with the video fade in and out without using sox?

---

