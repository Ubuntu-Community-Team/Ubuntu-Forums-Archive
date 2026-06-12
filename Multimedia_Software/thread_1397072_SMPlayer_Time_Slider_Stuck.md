---
title: "SMPlayer Time Slider Stuck"
date: 2010-02-02
forum: Multimedia Software
---

### Post by MrDelish on 2010-02-02
Very odd problem I'm having with SMPlayer on 9.10 64-bit. I made sure to use the PPAs from Launchpad ([https://launchpad.net/~rvm](https://launchpad.net/~rvm)) to get the newer versions of MPlayer and SMPlayer, but when I open certain videos (particularly AVI files), the time slider stays at the very beginning. I can pause and resume, but I'm not able to see how much time is left on the video and any attempts to move ahead restart the video from the beginning. I found a thread discussing a similar issue ([http://ubuntuforums.org/showthread.php?t=1365247](http://ubuntuforums.org/showthread.php?t=1365247)), but changing the sound output didn't help.

Any suggestions?

---

### Post by rvm4000 on 2010-02-02
Maybe smplayer has problems to read the output of mplayer. Can you copy the mplayer log (options -> view logs) when playing one of these videos?

---

### Post by MrDelish on 2010-02-02
Thanks for the response. Here's the mplayer log output:

```
/usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo gl:yuv=2:force-pbo:ati-hack -ao pulse -nokeepaspect -framedrop -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 58720271 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/user/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -subpos 100 -volume 50 -cache 2000 -osdlevel  -vf-add pp -autoq 6 -vf-add eq2,hue -vf-add screenshot -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /media/mvi_0925.avi

MPlayer SVN-r29643-Ubuntu-RVM (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing /media/mvi_0925.avi.

Cache fill:  0.00% (0 bytes)   
AVI file format detected.
ID_VIDEO_ID=0
[aviheader] Video stream found, -vid 0
ID_AUDIO_ID=1
[aviheader] Audio stream found, -aid 1
VIDEO:  [MJPG]  640x480  24bpp  30.000 fps  2101.5 kbps (256.5 kbyte/s)
Clip info:
 Digitization Time: THU JAN 07 09:41:57 2010

ID_CLIP_INFO_NAME0=Digitization Time
ID_CLIP_INFO_VALUE0=THU JAN 07 09:41:57 2010

 Software: CanonMVI06
ID_CLIP_INFO_NAME1=Software
ID_CLIP_INFO_VALUE1=CanonMVI06
ID_CLIP_INFO_N=2
ID_FILENAME=/media/mvi_0925.avi
ID_DEMUXER=avi
ID_VIDEO_FORMAT=MJPG
ID_VIDEO_BITRATE=2101456
ID_VIDEO_WIDTH=640
ID_VIDEO_HEIGHT=480
ID_VIDEO_FPS=30.000
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=1
ID_AUDIO_BITRATE=705600
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_LENGTH=0.03
ID_SEEKABLE=1
ID_CHAPTERS=0
[gl] using extended formats. Use -vo gl:nomanyfmts if playback fails.
Couldn't open video filter '***'.
***: cannot add video filter
Opening video filter: [screenshot]
Opening video filter: [hue]
Opening video filter: [eq2]
Opening video filter: [pp]
[***] Init
[***] Updating font cache.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat -1
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG)
==========================================================================
ID_VIDEO_CODEC=ffmjpeg
[PP] Using external postprocessing filter, max q = 6.
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 44100 Hz, 1 ch, s16le, 705.6 kbit/100.00% (ratio: 88200->88200)
ID_AUDIO_BITRATE=705600
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=1
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [pulse] 44100Hz 1ch floatle (4 bytes per sample)
ID_AUDIO_CODEC=pcm
[Mixer] No hardware mixing, inserting volume filter.
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar 422P)
[PP] Using external postprocessing filter, max q = 6.
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar 422P as output csp (no 1)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 9 -> 8
[swscaler @ 0xe6ff60]BICUBIC scaler, from yuv422p to yuv420p using MMX2
[swscaler @ 0xe6ff60]using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0xe6ff60]using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0xe6ff60]using 1-tap MMX "scaler" for vertical scaling (YV12 like)
[swscaler @ 0xe6ff60]640x480 -> 640x480
[swscaler @ 0xe6ff60]No accelerated colorspace conversion found.
VO: [gl] 640x480 => 640x480 Planar YV12 
X11 error: BadMatch (invalid parameter attributes)
ID_VIDEO_TRACK=0
ID_AUDIO_TRACK=1
```

---

### Post by rvm4000 on 2010-02-03
The length of the video should be wrong, mplayer reports **ID_LENGTH=0.03**.

You'll probably need to use the mplayer option -forceidx to be able to seek in that video.

---

