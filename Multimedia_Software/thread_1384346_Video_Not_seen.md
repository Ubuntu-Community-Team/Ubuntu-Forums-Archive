---
title: "Video Not seen"
date: 2010-01-18
forum: Multimedia Software
---

### Post by prap19 on 2010-01-18
I am not able to see the video of a .flv format in VLC player. I tried it in the SMplayer also but of no use. I can hear the audio but no video on it. Just a black screen. Could anyone tell me what could be the problem?

---

### Post by rvm4000 on 2010-01-18
Copy here the mplayer log after trying to play the flv (options -> view logs).

---

### Post by prap19 on 2010-01-25
Mplayer log (Sorry if i hav included too much than required. I m a super amateur)

```
/usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv -ao alsa -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 62914575 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/prasad/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -aid 1 -subpos 100 -volume 40 -cache 2000 -ss 442 -osdlevel 0 -vf-add screenshot -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /home/prasad/Desktop/RobertFull-NaturalRobots.flv

MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing /home/prasad/Desktop/RobertFull-NaturalRobots.flv.

Cache fill: 12.00% (245760 bytes)   
libavformat file format detected.
ID_VIDEO_ID=0
[lavf] Video stream found, -vid 0
ID_AUDIO_ID=1
[lavf] Audio stream found, -aid 1
VIDEO:  [FLV1]  320x178  0bpp  29.917 fps  254.7 kbps (31.1 kbyte/s)
ID_FILENAME=/home/prasad/Desktop/RobertFull-NaturalRobots.flv
ID_DEMUXER=lavfpref
ID_VIDEO_FORMAT=FLV1
ID_VIDEO_BITRATE=254680
ID_VIDEO_WIDTH=320
ID_VIDEO_HEIGHT=178
ID_VIDEO_FPS=29.917
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=85
ID_AUDIO_BITRATE=64000
ID_AUDIO_RATE=22050
ID_AUDIO_NCH=1
ID_LENGTH=1255.49
ID_SEEKABLE=1
ID_CHAPTERS=0
[***] auto-open
Opening video filter: [screenshot]
[***] Init
[***] Updating font cache.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffflv] vfm: ffmpeg (FFmpeg Flash video)
==========================================================================
ID_VIDEO_CODEC=ffflv
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 22050 Hz, 2 ch, s16le, 64.0 kbit/9.07% (ratio: 8000->88200)
ID_AUDIO_BITRATE=64000
ID_AUDIO_RATE=22050
ID_AUDIO_NCH=2
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[equalizer] Limiting the number of filters to 9 due to low sample rate.
[equalizer] Limiting the number of filters to 9 due to low sample rate.
[equalizer] Limiting the number of filters to 9 due to low sample rate.
AO: [alsa] 22050Hz 2ch floatle (4 bytes per sample)
[equalizer] Limiting the number of filters to 9 due to low sample rate.
[equalizer] Limiting the number of filters to 9 due to low sample rate.
ID_AUDIO_CODEC=mp3
[Mixer] No hardware mixing, inserting volume filter.
[equalizer] Limiting the number of filters to 9 due to low sample rate.
Starting playback...
VDec: vo config request - 320 x 178 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0xfa2240]No accelerated colorspace conversion found.
[swscaler @ 0xfa2240]using unscaled yuv420p -> rgb24 special converter
VO: [xv] 320x178 => 320x178 Planar YV12 
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)
```

---

### Post by rvm4000 on 2010-01-25
It seems there's some kind of problem with the *xv* output. Go to the smplayer preferences, and select another video output (gl, x11...) in general -> video.

---

### Post by prap19 on 2010-01-26
Hey thanks the problem got solved!

---

