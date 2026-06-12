---
title: "Cant play videos with mplayer/mplayer2"
date: 2013-03-16
forum: Multimedia Software
---

### Post by linuxyogi on 2013-03-16
I am using Nvidia 9500GT with 1 gb vram.

The Nvidia proprietary driver is installed. 

I am using vdpau with smplayer. Previously it had played HD videos with vdpau just fine but today it won't.

I tried the uninstalling mplayer2 & installed mplayer but same error. I have tried playing multiple videos. The videos are playing fine in vlc.



```
/usr/bin/mplayer -noquiet -nofs -nomouseinput -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau,ffodivxvdpau, -sub-fuzziness 1 -identify -slave -vo vdpau -ao alsa -nokeepaspect -framedrop -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 56623149 -monitorpixelaspect 1 -ass -embeddedfonts -ass-line-spacing 0 -ass-font-scale 1 -ass-styles /home/tux/.config/smplayer/styles.ass -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -aid 0 -subpos 100 -volume 100 -nocache -ss 799 -osdlevel 0 -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 300 /home/tux/video.mp4

MPlayer2 UNKNOWN (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing /home/tux/video.mp4.
Detected file format: QuickTime/MPEG-4/Motion JPEG 2000 format (libavformat)
ID_VIDEO_ID=0
[lavf] stream 0: video (h264), -vid 0
ID_AUDIO_ID=0
ID_AID_0_LANG=und
[lavf] stream 1: audio (aac), -aid 0, -alang und
ID_AUDIO_ID=1
ID_AID_1_LANG=und
[lavf] stream 2: audio (aac), -aid 1, -alang und
VIDEO:  [H264]  1280x528  24bpp  23.976 fps  2298.8 kbps (280.6 kbyte/s)
Clip info:
 major_brand: mp42
ID_CLIP_INFO_NAME0=major_brand
ID_CLIP_INFO_VALUE0=mp42
 minor_version: 0
ID_CLIP_INFO_NAME1=minor_version
ID_CLIP_INFO_VALUE1=0
 compatible_brands: isomavc1mp42
ID_CLIP_INFO_NAME2=compatible_brands
ID_CLIP_INFO_VALUE2=isomavc1mp42
 creation_time: 2010-09-05 19:30:29
ID_CLIP_INFO_NAME3=creation_time
ID_CLIP_INFO_VALUE3=2010-09-05 19:30:29
ID_CLIP_INFO_N=4
Load subtitles in /home/tux/
ID_FILENAME=/home/tux/video.mp4
ID_DEMUXER=lavfpref
ID_VIDEO_FORMAT=H264
ID_VIDEO_BITRATE=2298808
ID_VIDEO_WIDTH=1280
ID_VIDEO_HEIGHT=528
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=2.4242
ID_AUDIO_FORMAT=MP4A
ID_AUDIO_BITRATE=124960
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
ID_START_TIME=0.00
ID_LENGTH=9469.50
ID_SEEKABLE=1
ID_CHAPTERS=0
==========================================================================
Forced video codec: ffh264vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
==========================================================================
ID_VIDEO_CODEC=ffh264vdpau
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 125.0 kbit/8.14% (ratio: 15620->192000)
ID_AUDIO_BITRATE=124960
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [alsa] 48000Hz 2ch floatle (4 bytes per sample)
ID_AUDIO_CODEC=ffaac
[Mixer] No hardware mixing, inserting volume filter.
Starting playback...
Movie-Aspect is 2.42:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=2.4242
VO: [vdpau] 1280x528 => 1280x528 H.264 VDPAU acceleration 
[vdpau] Got display refresh rate 60.000 Hz.
[vdpau] If that value looks wrong give the -vo vdpau:fps=X suboption manually.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.

[   vdpau] Failed creating VDPAU decoder: A catch-all error, used when no other error code applies.
```

---

### Post by andrew.46 on 2013-03-16
Looks like an NVidia/vdpau issue. Try:

```
mplayer -vo xv /home/tux/video.mp4
```

and this will probably play ok...

---

### Post by sudodus on 2013-03-16
This alias works for me now with an up-to-date Ubuntu 12.04.2 running lubuntu-desktop
```
alias mplayervdpau='mplayer -vo vdpau -vc ffh264vdpau -lavdopts skiploopfilter=nonref -use-filename-title -fs'
```
Which version of Ubuntu and the proprietary nvidia driver are you running?

---

### Post by linuxyogi on 2013-03-16
> **sudodus said:**
> This alias works for me now with an up-to-date Ubuntu 12.04.2 running lubuntu-desktop
```
alias mplayervdpau='mplayer -vo vdpau -vc ffh264vdpau -lavdopts skiploopfilter=nonref -use-filename-title -fs'
```
Which version of Ubuntu and the proprietary nvidia driver are you running?

I am running Xubuntu 12.04
Nvidia Driver Version : 295.40

---

### Post by linuxyogi on 2013-03-16
> **andrew.46 said:**
> Looks like an NVidia/vdpau issue. Try:

```
mplayer -vo xv /home/tux/video.mp4
```

and this will probably play ok...

But that will put heavy load on the cpu.

---

### Post by sudodus on 2013-03-16
> **linuxyogi said:**
> I am running Xubuntu 12.04
Nvidia Driver Version : 295.40
This is the same ubuntu version and the same nvidia driver. I have a GeForce GT 430/PCIe card, which works.

Can you remember something that could have happened to your system? Maybe you should check the video clip or try another one. Maybe you should check that your root partition is good (with no corrupted files).

... or could it be a hardware error?

---

### Post by linuxyogi on 2013-03-16
> **sudodus said:**
> This is the same ubuntu version and the same nvidia driver. I have a GeForce GT 430/PCIe card, which works.

Can you remember something that could have happened to your system? Maybe you should check the video clip or try another one. Maybe you should check that your root partition is good (with no corrupted files).

... or could it be a hardware error?

No I don't remember anything that might have disabled vdpau. I have tried many video clips. How do I check the root partition for errors ?
Never done that before manually.

If its a hardware error I will be really sorry.

---

### Post by andrew.46 on 2013-03-16
> **linuxyogi said:**
> But that will put heavy load on the cpu.

Possibly but it will confirm that your installation of MPlayer is working ok :)

---

### Post by linuxyogi on 2013-03-16
> **andrew.46 said:**
> Possibly but it will confirm that your installation of MPlayer is working ok :)

I just tried with xv & its playing okay.

---

### Post by sudodus on 2013-03-16
> **linuxyogi said:**
> No I don't remember anything that might have disabled vdpau. I have tried many video clips. How do I check the root partition for errors ?
Never done that before manually.

If its a hardware error I will be really sorry.

Run ***df*** in your installed Ubuntu system to identify your root partition: the device **/dev/sd[COLOR=#ff0000]xy[/COLOR]** that is mounted on **/**

Boot linux from another drive, for example from an Ubuntu install drive.

Find out which device is your root partition (it is probably the same as last time, but it may have changed device letter).

Check with ***df*** that no partition on your internal drive is mounted. Unmount if necessary. Run
```
sudo e2fsck -f /dev/sdxy 
``` where x is the device letter and y is the partition number, maybe /dev/sda1 or /dev/sda6

---

### Post by linuxyogi on 2013-03-16
```
tux@mypc:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda4       89514184 12503560  72463552  15% /
udev             1016700        4   1016696   1% /dev
tmpfs             410200      804    409396   1% /run
none                5120        0      5120   0% /run/lock
none             1025496       84   1025412   1% /run/shm
/dev/sda2       61337596 30270280  31067316  50% /media/E6B8B6F8B8B6C5F9
```


```
root@PartedMagic:~# e2fsck -f /dev/sda4
e2fsck 1.41.14 (22-Dec-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda4: 221081/5685248 files (0.3% non-contiguous), 3482530/22735360 blocks
```

Then tried playing again but same thing.

---

### Post by sudodus on 2013-03-16
The file system looks good, it did not cause the problem. We still hope it is a software error. So boot again from an external drive, but not from the parted magic rescue drive, but from the Ubuntu install drive (ideally from a version 12.04.2 drive). Run a live session and install the nvidia driver into the live session (using jockey-gtk).

I don't remember if it is necessary to restart the graphics (the x-session) to get the new driver active, but in that case, start a text screen with ***ctrl + alt + F1*** and from there run

```
sudo service lightdm stop
```
```
sudo service lightdm start
```

You will probably find the graphic screen with ***ctrl + alt + F7*** 

Try to run mplayer/mplayer2 with vdpau in this live session. If it works, you can be sure there is a software error in your installed system.

---

### Post by linuxyogi on 2013-03-16
@[**[COLOR=#000000]sudodus[/COLOR]**]("http://ubuntuforums.org/member.php?u=1499021")

I have a xubuntu 12.04 cd with me so it booted in live mode & started jockey-gtk but strangely it didn't detect my card.

---

### Post by sudodus on 2013-03-16
I'll try with my old install CD (not sub-version .2). So I will be off-line for a while.

---

### Post by linuxyogi on 2013-03-16
> **sudodus said:**
> I'll try with my old install CD (not sub-version .2). So I will be off-line for a while.

Okay.

---

### Post by linuxyogi on 2013-03-16
I just booted in Win7, played a game, played the same HD videos in WMP. CPU usage ranged from 5-22% so it means it is utilizing pure video hd (the equivalent of vdpau).

---

### Post by andrew.46 on 2013-03-16
Try reinstalling your nvidia driver and vdpau. As a sidenote: You might actually find that if you have a reasonably fast cpu hardware acceleration from the GPU is not such a big deal, although gaming tends to be a deal breaker for this. I have quite a fast processor:

```

andrew@skamandros~$ uname -p
AMD FX(tm)-8350 Eight-Core Processor

```

and for video clips etc vdpau does not seem to be critical.

---

### Post by mc4man on 2013-03-16
Maybe ck. your vdpau status - 

sudo apt-get install vdpauinfo
vdpauinfo

---

### Post by andrew.46 on 2013-03-16
> **sudodus said:**
> This alias works for me now with an up-to-date Ubuntu 12.04.2 running lubuntu-desktop
```
alias mplayervdpau='mplayer -vo vdpau -vc ffh264vdpau -lavdopts skiploopfilter=nonref -use-filename-title -fs'
```
Which version of Ubuntu and the proprietary nvidia driver are you running?

You might be interested in adding this to ~/.mplayer/config rather than running a bash alias? My own setting is reasonably conservative:

```

# If I use vdpau I prefer these video codecs:
#--------------
[vo.vdpau]
vc=ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau,ffh264vdpau,ffodivxvdpau,

```

but you could add your own settings in as well. I do it this way as I do not necessarily want to run vdpau by *default.*..

---

### Post by linuxyogi on 2013-03-16
I reinstalled Xubuntu. Vdpau is working now. Thanks to both.

---

### Post by andrew.46 on 2013-03-16
Good to hear that the issue is resolved :)

---

### Post by sudodus on 2013-03-17
> **linuxyogi said:**
> I reinstalled Xubuntu. Vdpau is working now. Thanks to both.
I'm glad you managed to get it running :KS but sad you needed to reinstall :-(

My adventure with the live Xubuntu was a failure. I have a clear memory of proprietary graphics being offered during live sessions, but it must have been before 12.04 (correct me if I'm wrong). And it is the same with persistent live systems. Now proprietary graphics is not even installable, at least I could not do it. I think that the way it is attached to the kernel is tighter now, so that the kernel is recompiled. And this is not possible in live systems. You can install packages, that are looser attached to the linux system, but you cannot change the kernel (at least not easily).

On the other hand it is quite easy to install the Ubuntu versions 12.04 and 12.10, I made a fresh install to a small test partition on my internal HDD, and found that mplayer2 was using vdpau for me without any support from my old environment. But I was delayed, and when I returned you had already done it yourself :-P

---

### Post by sudodus on 2013-03-17
> **andrew.46 said:**
> You might be interested in adding this to ~/.mplayer/config rather than running a bash alias? My own setting is reasonably conservative:

```

# If I use vdpau I prefer these video codecs:
#--------------
[vo.vdpau]
vc=ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau,ffh264vdpau,ffodivxvdpau,

```

but you could add your own settings in as well. I do it this way as I do not necessarily want to run vdpau by *default.*..

Thanks for the tips :-)

I have a few things in the config file, but run a lot directly from the command line. And for lighter video clips, I can use mplayer without any vdpau or other options. Anyway I use a couple of aliases. My workstation with 2x2 xeon processors plays the videos better (for example less stuttering) without vdpau in some cases. 1920x1080 50p HD video directly from my camera plays well with and without vdpau in LXDE, but only well without vdpau in XFCE.

---

### Post by andrew.46 on 2013-03-17
By using a *profile* in this way you do not actually get vdpau as your default video output :).

---

### Post by sudodus on 2013-03-17
> **andrew.46 said:**
> By using a *profile* in this way you do not actually get vdpau as your default video output :).
I will look into it and learn how it works :-)

---

### Post by andrew.46 on 2013-03-17
Man page has the details:

```

PROFILES
       To ease working with different configurations profiles can be defined in the con-
       figuration  files.   A profile starts with its name between square brackets, e.g.
       '[my-profile]'.  All following options will be part of the profile.   A  descrip-
       tion  (shown  by  -profile help) can be defined with the profile-desc option.  To
       end the profile, start another one or use the profile name 'default' to  continue
       with normal options.

       EXAMPLE MPLAYER PROFILE:

       [protocol.dvd]
       profile-desc="profile for dvd:// streams"
       vf=pp=hb/vb/dr/al/fd
       alang=en

       [protocol.dvdnav]
       profile-desc="profile for dvdnav:// streams"
       profile=protocol.dvd
       mouse-movements=yes
       nocache=yes

       [extension.flv]
       profile-desc="profile for .flv files"
       flip=yes

       [vo.pnm]
       outdir=/tmp

       [ao.alsa]
       device=spdif

       EXAMPLE MENCODER PROFILE:

       [mpeg4]
       profile-desc="MPEG4 encoding"
       ovc=lacv=yes
       lavcopts=vcodec=mpeg4:vbitrate=1200

       [mpeg4-hq]
       profile-desc="HQ MPEG4 encoding"
       profile=mpeg4
       lavcopts=mbd=2:trell=yes:v4mv=yes

```

Lots of possibilities there, my own usage is a little primitive, I have always meant to spend some more time with this...

---

