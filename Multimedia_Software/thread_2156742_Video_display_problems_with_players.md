---
title: "Video display problems with players"
date: 2013-06-22
forum: Multimedia Software
---

### Post by Jessfarnsworth on 2013-06-22
All my player options Smplayer and mplayer; and Vlc player dont want to display the video when played most of the time.  Sometimes though they playt fine.  I have tried many output options and x11 is slow, while xv works great when it works.  I have to shut down and restart and sometimes it works, and sometimes I uninstall and re-install and get it to work...This time, neither is working.  Any ideas will help.  I am runing and optiplex mmx4 intell.  Onboard video.  Thanks for your help.

---

### Post by Jessfarnsworth on 2013-06-23
M player is eating a ton of cpu over 80 percent and giving a bad allocation error, insufficent resources.  I am running nothing else but the default op sys progs.  What the heck is going on
?
\

---

### Post by Jessfarnsworth on 2013-06-23
I thought it might be the post processing which I had set to max, and I turned it off, and its still the same.  and after a reinstall of both smplayer and mplayer I still get the same error in mplayer.

---

### Post by Jessfarnsworth on 2013-06-23
my mplayer log.  I remmoved redundant bad allocation r3emarks.
/usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv -ao alsa -nokeepaspect -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 60817453 -monitorpixelaspect 1 -ass -embeddedfonts -ass-line-spacing 0 -ass-font-scale 1 -ass-styles /home/jess/.config/smplayer/styles.ass -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -aid 0 -subpos 100 -brightness 15 -saturation 20 -volume 40 -cache 5000 -ss 185 -osdlevel 0 -idx -vf-add yadif -vf-add pp -autoq 1 -vf-add eq2,hue -noslices -channels 2 -af volnorm=1,scaletempo,equalizer=4:8.8:9.1:6:4:8.8:7.3:7.6:6.4:4 -softvol -softvol-max 94 /media/JESSDRIVE C/Burn Notice S06E13 HDTV x264-ASAP[ettv]/Burn.Notice.S06E13.HDTV.x264-ASAP.mp4


MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.


Playing /media/JESSDRIVE C/Burn Notice S06E13 HDTV x264-ASAP[ettv]/Burn.Notice.S06E13.HDTV.x264-ASAP.mp4.


Cache fill:  0.00% (0 bytes)   


libavformat version 53.21.1 (external)
Mismatching header version 53.19.0
libavformat file format detected.
ID_VIDEO_ID=0
[lavf] stream 0: video (h264), -vid 0
ID_AUDIO_ID=0
[lavf] stream 1: audio (aac), -aid 0, -alang und
VIDEO:  [H264]  720x402  24bpp  23.976 fps  1083.3 kbps (132.2 kbyte/s)
Clip info:
 major_brand: isom
ID_CLIP_INFO_NAME0=major_brand
ID_CLIP_INFO_VALUE0=isom
 minor_version: 1
ID_CLIP_INFO_NAME1=minor_version
ID_CLIP_INFO_VALUE1=1
 compatible_brands: isom
ID_CLIP_INFO_NAME2=compatible_brands
ID_CLIP_INFO_VALUE2=isom
 creation_time: 2011-09-08 11:43:25
ID_CLIP_INFO_NAME3=creation_time
ID_CLIP_INFO_VALUE3=2011-09-08 11:43:25
ID_CLIP_INFO_N=4
Load subtitles in /media/JESSDRIVE C/Burn Notice S06E13 HDTV x264-ASAP[ettv]/
ID_FILENAME=/media/JESSDRIVE C/Burn Notice S06E13 HDTV x264-ASAP[ettv]/Burn.Notice.S06E13.HDTV.x264-ASAP.mp4
ID_DEMUXER=lavfpref
ID_VIDEO_FORMAT=H264
ID_VIDEO_BITRATE=1083312
ID_VIDEO_WIDTH=720
ID_VIDEO_HEIGHT=402
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=1.7910
ID_AUDIO_FORMAT=MP4A
ID_AUDIO_BITRATE=131576
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
ID_START_TIME=0.00
ID_LENGTH=2524.69
ID_SEEKABLE=1
ID_CHAPTERS=0
Opening video filter: [ass auto=1]
[ass] auto-open
Opening video filter: [hue]
Opening video filter: [eq2]
Opening video filter: [pp]
Opening video filter: [yadif]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
ID_VIDEO_CODEC=ffh264
[PP] Using external postprocessing filter, max q = 6.
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 131.6 kbit/8.57% (ratio: 16447->192000)
ID_AUDIO_BITRATE=131576
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [alsa] 48000Hz 2ch floatle (4 bytes per sample)
ID_AUDIO_CODEC=ffaac
[Mixer] No hardware mixing, inserting volume filter.
Starting playback...
Cache not responding! [performance issue]
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Unsupported PixelFormat 81
[PP] Using external postprocessing filter, max q = 6.
Movie-Aspect is 1.79:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=1.7910
VO: [xv] 720x402 => 720x402 Planar YV12 


X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)


Alloc (insufficient resources for operation)




X11 error: BadAlloc (insufficient resources for operation)




           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************


Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.




X11 error: BadAlloc (insufficient resources for operation)


X11 error: BadAlloc (insufficient resources for operation)

now everybody to the tune of Smoot Operater: "She's a bad allocotor, baaad allocator."
ha ha ha need sleep

---

### Post by Jessfarnsworth on 2013-06-23
Oh, and I tried totm, it game ve an aw4som picture, but the frams were droping several at a time.  It results in a goofy layback where you see the action step by step.  Thanks

---

### Post by Jessfarnsworth on 2013-06-23
I have compiled all my posts from overnight into one listing: here it is:

[LIST]
[*]**[IMG]http://ubuntuforums.org/images/icons/icon4.png[/IMG] Video display problems with players**

[INDENT]All my player options Smplayer and mplayer; and Vlc player don't want to display the video when played most of the time. Sometimes though they play fine. I have tried many output options and x11 is slow, while xv works great when it works. I have to shut down and restart and sometimes it works, and sometimes I uninstall and re-install and get it to work...This time, neither is working. Any ideas will help. I am runing and optiplex mmx4 intell. Onboard video. Thanks for your help.[/INDENT]

[*]

**Re: Video display problems with players**

[INDENT]M player is eating a ton of cpu over 80 percent and giving a bad allocation error, insufficent resources. I am running nothing else but the default op sys progs. What the heck is going on[#3]("http://ubuntuforums.org/showthread.php?t=2156742&p=12702699#post12702699")[/INDENT]

[*][[COLOR=#000000]Jessfarnsworth[/COLOR]]("http://ubuntuforums.org/member.php?u=1805612") 

[INDENT]I thought it might be the post processing which I had set to max, and I turned it off, and its still the same. and after a reinstall of both smplayer and mplayer I still get the same error in mplayer.[/INDENT]

[*]
[INDENT]my mplayer log. I remmoved redundant bad allocation r3emarks.
/usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv -ao alsa -nokeepaspect -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 60817453 -monitorpixelaspect 1 -ass -embeddedfonts -ass-line-spacing 0 -ass-font-scale 1 -ass-styles /home/jess/.config/smplayer/styles.ass -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -aid 0 -subpos 100 -brightness 15 -saturation 20 -volume 40 -cache 5000 -ss 185 -osdlevel 0 -idx -vf-add yadif -vf-add pp -autoq 1 -vf-add eq2,hue -noslices -channels 2 -af volnorm=1,scaletempo,equalizer=4:8.8:9.1:6:4:8.8:7 .3:7.6:6.4:4 -softvol -softvol-max 94 /media/JESSDRIVE C/Burn Notice S06E13 HDTV x264-ASAP[ettv]/Burn.Notice.S06E13.HDTV.x264-ASAP.mp4


MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.


Playing /media/JESSDRIVE C/Burn Notice S06E13 HDTV x264-ASAP[ettv]/Burn.Notice.S06E13.HDTV.x264-ASAP.mp4.


Cache fill: 0.00% (0 bytes) 


libavformat version 53.21.1 (external)
Mismatching header version 53.19.0
libavformat file format detected.
ID_VIDEO_ID=0
[lavf] stream 0: video (h264), -vid 0
ID_AUDIO_ID=0
[lavf] stream 1: audio (aac), -aid 0, -alang und
VIDEO: [H264] 720x402 24bpp 23.976 fps 1083.3 kbps (132.2 kbyte/s)
Clip info:
major_brand: isom
ID_CLIP_INFO_NAME0=major_brand
ID_CLIP_INFO_VALUE0=isom
minor_version: 1
ID_CLIP_INFO_NAME1=minor_version
ID_CLIP_INFO_VALUE1=1
compatible_brands: isom
ID_CLIP_INFO_NAME2=compatible_brands
ID_CLIP_INFO_VALUE2=isom
creation_time: 2011-09-08 11:43:25
ID_CLIP_INFO_NAME3=creation_time
ID_CLIP_INFO_VALUE3=2011-09-08 11:43:25
ID_CLIP_INFO_N=4
Load subtitles in /media/JESSDRIVE C/Burn Notice S06E13 HDTV x264-ASAP[ettv]/
ID_FILENAME=/media/JESSDRIVE C/Burn Notice S06E13 HDTV x264-ASAP[ettv]/Burn.Notice.S06E13.HDTV.x264-ASAP.mp4
ID_DEMUXER=lavfpref
ID_VIDEO_FORMAT=H264
ID_VIDEO_BITRATE=1083312
ID_VIDEO_WIDTH=720
ID_VIDEO_HEIGHT=402
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=1.7910
ID_AUDIO_FORMAT=MP4A
ID_AUDIO_BITRATE=131576
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
ID_START_TIME=0.00
ID_LENGTH=2524.69
ID_SEEKABLE=1
ID_CHAPTERS=0
Opening video filter: [ass auto=1]
[ass] auto-open
Opening video filter: [hue]
Opening video filter: [eq2]
Opening video filter: [pp]
Opening video filter: [yadif]
================================================== ========================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
================================================== ========================
ID_VIDEO_CODEC=ffh264
[PP] Using external postprocessing filter, max q = 6.
================================================== ========================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 131.6 kbit/8.57% (ratio: 16447->192000)
ID_AUDIO_BITRATE=131576
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
================================================== ========================
AO: [alsa] 48000Hz 2ch floatle (4 bytes per sample)
ID_AUDIO_CODEC=ffaac
[Mixer] No hardware mixing, inserting volume filter.
Starting playback...
Cache not responding! [performance issue]
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Unsupported PixelFormat 81
[PP] Using external postprocessing filter, max q = 6.
Movie-Aspect is 1.79:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=1.7910
VO: [xv] 720x402 => 720x402 Planar YV12 


X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)


Alloc (insufficient resources for operation)




X11 error: BadAlloc (insufficient resources for operation)




************************************************
**** Your system is too SLOW to play this! ****
************************************************


Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
- Try -ao sdl or use the OSS emulation of ALSA.
- Experiment with different values for -autosync, 30 is a good start.
- Slow video output
- Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
- Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
- Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
- Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
- Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.




X11 error: BadAlloc (insufficient resources for operation)


X11 error: BadAlloc (insufficient resources for operation)

now everybody to the tune of Smoot Operater: "She's a bad allocotor, baaad allocator."
ha ha ha need sleep[/INDENT]
[/LIST]

---

### Post by lisati on 2013-06-23
Threads merged.

Please use [noparse]```
 and 
```[/noparse] tags around long quotes.....

---

### Post by SeijiSensei on 2013-06-23
What if you disable the loop filter?  In smplayer, go to Options > Preferences > Performance and try disabling it.  

H.264 HD resolutions and older Intel motherboard graphics can be a match made in hell.  Your experiences are not uncommon. I bought an NVIDIA card at one time just so I could watch H.264 releases using VDPAU.

---

### Post by Jessfarnsworth on 2013-06-23
Ill give it a try.  I don't understand what looping does. II am a bit of aa noob when it omes to these things.

---

### Post by SeijiSensei on 2013-06-23
Here's a fairly non-technical explanation that applies to smplayer: [http://www.avsforum.com/t/1342634/video-issues-with-linux/30#post_20661217](http://www.avsforum.com/t/1342634/video-issues-with-linux/30#post_20661217)

---

### Post by Jessfarnsworth on 2013-06-23
Thanks guys for the help.  I have the cache set up higher and did the loop back disallow thing, now it just takes time to see if it solves my problem.

Jess

---

### Post by Jessfarnsworth on 2013-06-23
well, disabled looping.  Looked at process monitor, noticed that when nothing else is even running, I am at times using 80 percent evenb though only 19-`11 percent i showing as being used.  I don't know if it will help but I attached a screen shot of the monitor.  Thanks for your help guys. I kind of thing Mplayer or something else is running somewhere and not being seen.

---

### Post by Jessfarnsworth on 2013-06-25
I seem to have found the problem not only with the video player but with laggy internet speeds.  Ubuntu one was running unannounced in the background and eating what it thought was free memory.  But it was not free memory.....it came at a price.  Thanks to everyone who tried to help.

---

