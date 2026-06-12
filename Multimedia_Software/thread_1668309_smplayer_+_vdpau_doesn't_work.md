---
title: "smplayer + vdpau doesn't work"
date: 2011-01-16
forum: Multimedia Software
---

### Post by Eithrial on 2011-01-16
Hi,
Ive installed Ubuntu 10.10 yesterday and after little work I managed HDMI video and audio to start working. Currently Im using VLC video player to watch movies with X11 codec, however it doesn't work well with hd records with lots of action, thats why I want to try using vdpau in smplayer, but after setting it to be used codec I get audio only without video.

My graphic crad is Nvidia G210m, I have newest nvidia drivers installed manually.

Any ideas how to install/get-to-work vdpau codec?

Thanks in advance for any help!

---

### Post by Eithrial on 2011-01-16
Reinstalling nvidia drivers solved the problem, however video is even more choppy than with x11 although there is a lot less cpu usage. Any ideas what can get vdpau working well?

---

### Post by cchhrriiss121212 on 2011-01-16
First check you have restricted-extras installed. If so:
Open the terminal from the accessories menu, then type smplayer. Try to play a file with vdpau enabled and post the output from the terminal window.

---

### Post by Eithrial on 2011-01-17
> **cchhrriiss121212 said:**
> First check you have restricted-extras installed. If so:
Open the terminal from the accessories menu, then type smplayer. Try to play a file with vdpau enabled and post the output from the terminal window.

There is no output beside this: "This is SMPlayer v. 06.9....."

I don't know if it helps but these are logs from mplayer(taken from SMPlayer):

Choppy video:
```

p, li { white-space: pre-wrap; } /usr/bin/mplayer -noquiet -nofs -nomouseinput -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau, -lavdopts threads=2 -sub-fuzziness 1 -identify -slave -vo vdpau -ao alsa -nokeepaspect -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 73400667 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/mateusz/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp enca:pl:ISO-8859-1 -vid 0 -aid 0 -subpos 100 -volume 44 -cache 50000 -osdlevel 0 -slices -channels 2 -af scaletempo -softvol -softvol-max 110 /media/2214B13671E56BE8/Atlanta.Thrashers.@.Carolina.Hurricanes.English.2011.01.09.HD.Stream.mp4
 
 MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
 mplayer: could not connect to socket
 mplayer: No such file or directory
 Failed to open LIRC support. You will not be able to use your remote control.
 
 Playing /media/2214B13671E56BE8/Atlanta.Thrashers.@.Carolina.Hurricanes.English.2011.01.09.HD.Stream.mp4.
 
 Cache fill:  0.00% (0 bytes)   
 Cache fill: 11.42% (5849088 bytes)   
 libavformat file format detected.
 [aac @ 0x1043c10]Transition from an ONLY_LONG or LONG_STOP to an EIGHT_SHORT sequence detected. If you heard an audible artifact, please submit the sample to the FFmpeg developers.
 ID_VIDEO_ID=0
 [lavf] stream 0: video (h264), -vid 0
 ID_AUDIO_ID=0
 ID_AID_0_LANG=und
 [lavf] stream 1: audio (aac), -aid 0, -alang und
 VIDEO:  [H264]  960x540  24bpp  30.000 fps  1499.6 kbps (183.1 kbyte/s)
 Clip info:
  major_brand: isom
 ID_CLIP_INFO_NAME0=major_brand
 ID_CLIP_INFO_VALUE0=isom
  minor_version: 512
 ID_CLIP_INFO_NAME1=minor_version
 ID_CLIP_INFO_VALUE1=512
  compatible_brands: isomiso2avc1mp41
 ID_CLIP_INFO_NAME2=compatible_brands
 ID_CLIP_INFO_VALUE2=isomiso2avc1mp41
  encoder: Lavf52.64.2
 ID_CLIP_INFO_NAME3=encoder
 ID_CLIP_INFO_VALUE3=Lavf52.64.2
 ID_CLIP_INFO_N=4
 ID_FILENAME=/media/2214B13671E56BE8/Atlanta.Thrashers.@.Carolina.Hurricanes.English.2011.01.09.HD.Stream.mp4
 ID_DEMUXER=lavfpref
 ID_VIDEO_FORMAT=H264
 ID_VIDEO_BITRATE=1499632
 ID_VIDEO_WIDTH=960
 ID_VIDEO_HEIGHT=540
 ID_VIDEO_FPS=30.000
 ID_VIDEO_ASPECT=0.0000
 ID_AUDIO_FORMAT=MP4A
 ID_AUDIO_BITRATE=117432
 ID_AUDIO_RATE=44100
 ID_AUDIO_NCH=2
 ID_START_TIME=0.00
 ID_LENGTH=6116.31
 ID_SEEKABLE=1
 Cache not responding!
 ID_CHAPTERS=0
 Cache not responding!
 Couldn't open video filter '***'.
 ***: cannot add video filter
 [***] Init
 [***] Updating font cache
 ==========================================================================
 Forced video codec: ffh264vdpau
 Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
 Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
 ==========================================================================
 ID_VIDEO_CODEC=ffh264vdpau
 ==========================================================================
 Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
 AUDIO: 44100 Hz, 2 ch, s16le, 117.4 kbit/8.32% (ratio: 14679->176400)
 ID_AUDIO_BITRATE=117432
 ID_AUDIO_RATE=44100
 ID_AUDIO_NCH=2
 Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
 ==========================================================================
 AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
 ID_AUDIO_CODEC=faad
 [Mixer] No hardware mixing, inserting volume filter.
 Starting playback...
 [VD_FFMPEG] Trying pixfmt=0.
 Movie-Aspect is undefined - no prescaling applied.
 VO: [vdpau] 960x540 => 960x540 H.264 VDPAU acceleration 
 [VD_FFMPEG] XVMC-accelerated MPEG-2.
 [h264_vdpau @ 0x7fe2077e0fe0]Cannot parallelize deblocking type 1, decoding such frames in sequential order
 

```


Audio, no video. In VLC Player video works. In SMPlayer even other codecs fail.

```

p, li { white-space: pre-wrap; } /usr/bin/mplayer -noquiet -nofs -nomouseinput -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau, -lavdopts threads=2 -sub-fuzziness 1 -identify -slave -vo vdpau -ao alsa -nokeepaspect -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 73400667 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/mateusz/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp enca:pl:ISO-8859-1 -vid 0 -aid 0 -subpos 100 -volume 44 -cache 50000 -osdlevel 0 -slices -channels 2 -af scaletempo -softvol -softvol-max 110 /media/Dog/winter/nhl.2011.winter.classic.capitals.vs.penguins.720p.hdtv.x264-orenji.mkv
 
 MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
 mplayer: could not connect to socket
 mplayer: No such file or directory
 Failed to open LIRC support. You will not be able to use your remote control.
 
 Playing /media/Dog/winter/nhl.2011.winter.classic.capitals.vs.penguins.720p.hdtv.x264-orenji.mkv.
 
 Cache fill:  0.00% (0 bytes)   
 libavformat file format detected.
 [matroska @ 0x1336f40]Estimating duration from bitrate, this may be inaccurate
 ID_AUDIO_ID=0
 [lavf] stream 0: audio (ac3), -aid 0
 ID_VIDEO_ID=0
 [lavf] stream 1: video (h264), -vid 0
 Clip info:
  doctype: matroska
 ID_CLIP_INFO_NAME0=doctype
 ID_CLIP_INFO_VALUE0=matroska
 ID_CLIP_INFO_N=1
 ID_FILENAME=/media/Dog/winter/nhl.2011.winter.classic.capitals.vs.penguins.720p.hdtv.x264-orenji.mkv
 ID_DEMUXER=lavfpref
 ID_AUDIO_FORMAT=8192
 ID_AUDIO_BITRATE=384000
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=6
 ID_START_TIME=0.00
 ID_LENGTH=7610.75
 ID_SEEKABLE=1
 ID_CHAPTERS=0
 ==========================================================================
 Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
 AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
 ID_AUDIO_BITRATE=384000
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
 ==========================================================================
 AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
 ID_AUDIO_CODEC=ffac3
 [Mixer] No hardware mixing, inserting volume filter.
 Video: no video
 Starting playback...
 
```

---

### Post by dazndom on 2011-01-17
I have the same problem, same graphics card but with Ubuntu driver.
i have just switched on highest graphics setting for 3d effects and now get what best can be described as a starry pattern across screen.
Also my screen for player is see thru, so i look at whatever is behind it, either desktop or firefox etc etc

gnomeplayer, vlc, rythtymbox etc all play just fine

i have just installed ffmpeg so as to make screencasts and during install it removed packages 
but i dunno what   !!??

love to find an answer

cheers Daz

---

### Post by cchhrriiss121212 on 2011-01-17
Try using this from a terminal:
```
mplayer -vo vdpau pathtoyourfile
```

---

### Post by Eithrial on 2011-01-18
That way it worked. 

```
mateusz@Bender:~$ mplayer -vo vdpau '/media/Dog/winter/nhl.2011.winter.classic.capitals.vs.penguins.720p.hdtv.x264-orenji.mkv' 
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /media/Dog/winter/nhl.2011.winter.classic.capitals.vs.penguins.720p.hdtv.x264-orenji.mkv.
libavformat file format detected.
[matroska @ 0x1f43ed0]Estimating duration from bitrate, this may be inaccurate
[lavf] stream 0: audio (ac3), -aid 0
[lavf] stream 1: video (h264), -vid 0
VIDEO:  [H264]  1280x720  0bpp  29.917 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 doctype: matroska
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [vdpau] 1280x720 => 1280x720 Planar YV12 
No bind found for key 'MOUSE_BTN2'.                         3% 10 0 
No bind found for key 'MOUSE_BTN2'.                         3% 10 0 
A:  10.6 V:  10.6 A-V:  0.000 ct:  0.000   0/  0 66%  8%  1.3% 10 0 
Exiting... (Quit)
```

What should I do to get by with those errors at the beginning of this log and how to fix smplayer?

---

### Post by cchhrriiss121212 on 2011-01-19
Try deleting any config files for smplayer, then reinstalling the package with synaptic. It is probably something in preferences that is causing the issue so try changing a few of those if the problem persists.

---

