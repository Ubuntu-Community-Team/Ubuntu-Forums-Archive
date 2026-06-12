---
title: "mencoder segfault"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by Pigeon. on 2008-01-23
Using mencoder 2:1.0~rc1-0ubuntu13.1 to transcode a large .m2t file recorded from kaffeine, I get a segfault after about 1.7GB:

```

mencoder Bull_Run.m2t -vf scale=352:198 -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=800 -o /tmp/bullrun-scaled.avi
MEncoder 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.40GHz (Family: 15, Model: 2, Stepping: 7)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0xda70b20
TS file format detected.
VIDEO MPEG2(pid=6785) AUDIO MPA(pid=6786) NO SUBS (yet)!  PROGRAM N. 1000
VIDEO:  MPEG2  544x576  (aspect 3)  25.000 fps  15000.0 kbps (1875.0 kbyte/s)
[V] filefmt:29  fourcc:0x10000002  size:544x576  fps:25.00  ftime:=0.0400
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [scale w=352 h=198]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 544 x 576 (preferred colorspace: Mpeg PES)
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
audiocodec: framecopy (format=50 chans=2 rate=48000 bits=16 B/s=24000 sample-1)
VDec: vo config request - 544 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
SwScaler: reducing / aligning filtersize 8 -> 8
SwScaler: reducing / aligning filtersize 8 -> 8
SwScaler: reducing / aligning filtersize 13 -> 12
SwScaler: reducing / aligning filtersize 13 -> 12

SwScaler: BICUBIC scaler, from yuv420p to yuv420p using MMX2
SwScaler: using 8-tap MMX scaler for horizontal luminance scaling
SwScaler: using 8-tap MMX scaler for horizontal chrominance scaling
SwScaler: using n-tap MMX scaler for vertical scaling (YV12 like)
SwScaler: 544x576 -> 352x198
videocodec: libavcodec (352x198 fourcc=34504d46 [FMP4])
Writing header...2f ( 0%)  0.00fps Trem:   0min   0mb  A-V:-0.004 [0:0]
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

1 duplicate frame(s)!
Pos:   0.8s     22f ( 0%)  0.00fps Trem:   0min   0mb  A-V:-0.084 [0:192]
1 duplicate frame(s)!
Pos:   1.3s     32f ( 0%)  0.00fps Trem:   0min   0mb  A-V:-0.084 [1173:192]
1 duplicate frame(s)!
Pos:   1.7s     42f ( 0%) 40.42fps Trem:   0min   0mb  A-V:-0.084 [1050:192]
1 duplicate frame(s)!
<snip a bunch of "duplicate frame" output>
Pos:  13.6s    312f ( 0%) 60.94fps Trem:  80min 1534mb  A-V:-0.084 [798:192]
1 duplicate frame(s)!
Pos:  14.1s    323f ( 0%) 61.26fps Trem:  80min 1528mb  A-V:-0.081 [784:192]
1 duplicate frame(s)!
Pos:4162.6s 104036f (28%) 64.98fps Trem:  66min 1730mb  A-V:0.080 [800:192]]
Skipping frame!
Segmentation faultf (32%) 65.58fps Trem:  62min 1727mb  A-V:0.039 [798:192]

```

The problem with performing any experimentation on this is that it takes a very long time because it gets so far through the file before the segfault, so any comments would be appreciated.

---

### Post by eye208 on 2008-01-23
You can start encoding at a time offset using the -ss option. This may help you test the critical part of the input file with different settings and codecs.

If there is a bug in lavc, you may be able to work around it by using -ovc xvid instead. Xvid encodes to MPEG-4 ASP format too.

If MPEG-4 ASP compatibility is not mandatory, use -ovc x264 instead which will give you MPEG-4 AVC (H.264). This will result in better quality at the same bitrate.

---

### Post by opscure on 2008-01-23
you could also script your way around it, in that when you have a seg fault just continue from the frame where you left off.  This is not neat, but should help you to at least compile your movie.

---

### Post by andrew.46 on 2008-01-24
Hi,

You could try the mplayer-users mailing list but I suspect that their advice will be to use the latest svn mplayer / mencoder. I have written a walkthrough for this if you are interested:

[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

 All the best,

    Andrew

---

### Post by Pigeon. on 2008-01-24
Cheers all, yes it does appear to be a libavcodec problem - using xvid seems to be OK, it's just frightfully slow (round about 15fps on a 2.4GHz Celeron). x264 also works but is even slower.

Next problem to solve is losing sync between sound and video. If I play the raw m2t with mplayer then sound and video are in sync, but somehow the transcoding seems to lose sync no matter what; playing the transcoded version with mplayer or trying to edit it in avidemux the sound and video are infuriatingly out of sync, by well over a second. Using -forceidx in the transcoding doesn't help, nor does transcoding to .mpg and allowing avidemux to build the index. I can correct it using the shift adjustment in avidemux but it is something of a pain trying to find the right setting, because of the way the brain processes such things, especially with small time differences.

I think I have much to learn about the whole subject of video files and coding... up until now I've had very little to do with it, and I'm learning more or less from scratch.

---

### Post by eye208 on 2008-01-24
I've had best results using MP4 instead of AVI. AVI is an old container format that doesn't really support many of today's stream formats. There have been ugly hacks to make it work with B-frames and VBR MP3, but these basically break the original specification.

MP4 has been designed for all kinds of MPEG video and audio formats. You can use MEncoder to encode raw MPEG-4 video and audio streams, then use MP4Box to mux these into a 100% spec compliant MP4 container. These can be played by MPlayer, VLC, Totem, Windows Media Player (using a DirectShow filter) and Quicktime (H.264 and AAC-LC), as well as many mobile devices.

See [here](http://ubuntuforums.org/showthread.php?p=4190924#post4190924) for an example. See [here](http://ubuntuforums.org/showthread.php?p=4075460#post4075460) for a quality comparison of MPEG-4 ASP (Xvid) vs. MPEG-4 AVC (H.264) at identical bitrates.

---

### Post by Pigeon. on 2008-01-25
Thanks, I'm trying that, no results yet though because it's only transcoding each pass at about 6fps and I've got a 4-hour file to process :(

In the meantime, even trying to edit the raw m2t with avidemux (2.4 r3731), I'm still getting it with sound and video way out of sync, and I mean massively so, several seconds wrong. mplayer will play the raw file fine, but in avidemux the sync is way off, and it (rather naturally) saves the edited version with the sync way off. Doing "Build VBR time map" as soon as I load the file into avidemux doesn't make any difference.

Also, trying to save as MP4 from avidemux I get something that mplayer refuses to play, something seems to be majorly incompatible in a big way:

```

[mpeg4 @ 0x88a96d8]only rectangular vol supported
Marker bit missing before time_increment_resolution
[mpeg4 @ 0x88a96d8]Static Sprites not supported
[mpeg4 @ 0x88a96d8]Complexity estimation not supported
[mpeg4 @ 0x88a96d8]only rectangular vol supported
Marker bit missing before time_increment_resolution
[mpeg4 @ 0x88a96d8]Static Sprites not supported
[mpeg4 @ 0x88a96d8]N-bit not supported
[mpeg4 @ 0x88a96d8]quant precision 13
[mpeg4 @ 0x88a96d8]Complexity estimation not supported
[mpeg4 @ 0x88a96d8]only rectangular vol supported
Marker bit missing before time_increment_resolution
Marker bit missing before fixed_vop_rate
[mpeg4 @ 0x88a96d8]Static Sprites not supported
[mpeg4 @ 0x88a96d8]Complexity estimation not supported
[mpeg4 @ 0x88a96d8]scalability not supported
[mpeg4 @ 0x88a96d8]only rectangular vol supported
[mpeg4 @ 0x88a96d8]Gray shape not supported
Marker bit missing before time_increment_resolution
[mpeg4 @ 0x88a96d8]N-bit not supported
[mpeg4 @ 0x88a96d8]quant precision 15
[mpeg4 @ 0x88a96d8]Complexity estimation not supported
[mpeg4 @ 0x88a96d8]reduced resolution VOP not supported
[mpeg4 @ 0x88a96d8]illegal chroma format
[mpeg4 @ 0x88a96d8]only rectangular vol supported
Marker bit missing before fixed_vop_rate
[mpeg4 @ 0x88a96d8]header damaged
Error while decoding frame!

```
...and so on.

Maybe I need to try building the latest svn version of mplayer instead of using the standard ubuntu version...

---

### Post by eye208 on 2008-01-25
> **Pigeon. said:**
> in fact with MP4 I get something that mplayer refuses to play, something seems to be majorly incompatible in a big way
I can confirm that.

If you use MEncoder to mux into MP4 (-of lavf -lavfopts format=mp4) the result will be broken too, i.e. Quicktime will be unable to open it.

MP4Box is the most reliable tool for MP4 muxing on Linux so far.

---

### Post by Pigeon. on 2008-01-25
It's a command line tool, though, unless I'm missing something in a very major way!!! I'm talking about brokenness in saving from avidemux after editing... And it's broken saving as AVI as well, mplayer plays video but no sound, and gives this on the console:

```

pigeon@pindix:~/lpntv$ mplayer nvs1a.avi
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.40GHz (Family: 15, Model: 2, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing nvs1a.avi.
AVI file format detected.

Badly interleaved AVI file detected - switching to -ni mode...
AVI: Missing video stream!? Contact the author, it may be a bug :(
MPEG-ES file format detected.
VIDEO:  MPEG2  544x576  (aspect 3)  25.000 fps  15000.0 kbps (1875.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
gnome_screensaver_control()==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 544 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 544 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 544x576 => 1024x576 Planar YV12 
gnome_screensaver_control().0% 0 0 
Exiting... (Quit)

```

---

### Post by eye208 on 2008-01-25
> **Pigeon. said:**
> I'm trying that, no results yet though because it's only transcoding each pass at about 6fps and I've got a 4-hour file to process
By the way, you can always use MEncoder's -ss and -endpos options to process only a short part of the video. This way you can verify your method before going for the whole file.

---

### Post by Pigeon. on 2008-01-26
Cheers... but I think we're missing my point a bit, probably my fault because I am suffering from severe sleep deprivation atm and I am having severe problems thinking...

While it may be true that mp4 is a better format than avi, avidemux is not capable of saving in it in a non-broken fashion, and it is avidemux that I am using to edit the video, because of the nice UI and the simple nature of the editing that I am doing; it seems pointless for me to thrash at trying to use a format which is in any case not properly compatible with the editor I am using.

I have found that if instead of simply using "copy" for the video and audio codecs in avidemux, but instead tell it to recode with xvid and mp3, then it saves an apparently non-broken avi, ie. mplayer can play it fine, and if I have corrected the A-V sync in avidemux before saving it, then mplayer plays it correctly synced, and if I reload it into avidemux it is still correctly synced. It is foully slow at saving, coding at around 5fps, but it works, which is the main thing.

I have also found that transcoding with mencoder does eventually segfault using both xvid and x264 codecs, but transcoding with avidemux/xvid does not segfault, so it seems to be mencoder rather than the codec that has the problem. As I have found an alternative method which does work, and I have stuff that I need to get done, I am relegating investigation of the segfault to the back burner for the time being, until I have done the important bit of the work.

The problem which is currently most awkward with the work is the loss of A-V sync. While it is possible to use avidemux's "shift" feature to correct the sync, it is a PITA to get it right; getting it nearly right is easy enough, but getting it spot on is very hard, as the brain ceases to be able to correctly analyse the time difference below a few hundred milliseconds and switches from reporting "sound in advance" or "sound retarded" to reporting little more than "that doesn't look right". 

But the loss of sync is not inevitable, as mplayer does play the raw m2t directly with correct sync; it is when I try and load it into avidemux to edit it that it loses sync. Furthermore, the shift of sync is not constant, but varies for different m2ts. It is to find out what causes this loss of sync and fix it that would currently be of most use.

---

### Post by eye208 on 2008-01-28
> **Pigeon. said:**
> But the loss of sync is not inevitable, as mplayer does play the raw m2t directly with correct sync; it is when I try and load it into avidemux to edit it that it loses sync. Furthermore, the shift of sync is not constant, but varies for different m2ts. It is to find out what causes this loss of sync and fix it that would currently be of most use.
What I find most interesting is the fact that MPlayer seems to play your files just fine while MEncoder crashes while reading them. These programs share the same code for demuxing and decoding after all.

There are two possible explanations for the loss of A/V sync:

[LIST=1]
[*]Editing the video in stream copy mode. As you probably know, audio compression uses frames, i.e. sample-accurate editing is impossible. Audio frame duration does not equal video frame duration, i.e. if you remove a certain number of frames, sync is lost.

[*]MPEG-2 TS supports variable frame rates. AVI does not.
[/LIST]
By the way, I used Gutsy's Avidemux to encode MP4 this weekend. The result worked fine with Totem, VLC, MPlayer and Flash 9.0. What settings did you use?

---

