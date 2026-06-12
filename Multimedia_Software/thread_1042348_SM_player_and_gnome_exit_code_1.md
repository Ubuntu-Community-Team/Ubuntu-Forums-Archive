---
title: "SM player and gnome exit code 1"
date: 2009-01-17
forum: Multimedia Software
---

### Post by hatalar205 on 2009-01-17
Hi.Everyone. When I try to watch something, the same thing happening again and again. The same problem happens with VLC and Caffeine. The video suddenly stops and the screen turn into a black one. 
My computer is DELL 6000, 1,5 GB ram, Ati Mobility Radeon 128 MB video, CPU:1.86 Pentium R) .Here is the code. Please help. This is very annoying.

/usr/bin/mplayer -noquiet -nofs -sub-fuzziness 2 -identify -slave -vo x11 -ao alsa -zoom -nokeepaspect -framedrop -autosync 100 -dr -nodouble -input conf=/usr/share/smplayer/input.conf -nostop-xscreensaver -wid 54525964 -monitorpixelaspect 1 -*** -embeddedfonts -***-color ffffff00 -***-border-color 00000000 -***-force-style Bold=1,Outline=1,Shadow=4,FontName=Sans,Fontsize=21 -fontconfig -font Sans Serif -subfont-autoscale 1 -***-font-scale 1 -subcp ISO-8859-9 -aid 1 -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -nocache -osdlevel 0 -idx -vf-add expand=:::::1.33333,harddup -vf-add screenshot -vf-add eq2,hue -channels 2 -af volnorm=2 /media/Yerel Disk 250/dene/mamma mia/Mamma Mia.avi -loop 0

MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1.86GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Option msglevel: Unknown suboption 5
Warning unknown option msglevel at line 9
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing /media/Yerel Disk 250/dene/mamma mia/Mamma Mia.avi.
AVI file format detected.
ID_VIDEO_ID=0
[aviheader] Video stream found, -vid 0
ID_AUDIO_ID=1
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  640x272  12bpp  25.000 fps  795.8 kbps (97.1 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.2 (build 2540/release)
ID_CLIP_INFO_NAME0=Software
ID_CLIP_INFO_VALUE0=VirtualDubMod 1.5.10.2 (build 2540/release)
ID_CLIP_INFO_N=1
SUB: Detected subtitle file format: subviewer
SUB: Read 1549 subtitles.
ID_FILE_SUB_ID=0
ID_FILE_SUB_FILENAME=/media/Yerel Disk 250/dene/mamma mia/Mamma Mia-En.srt
SUB: Added subtitle file (1): /media/Yerel Disk 250/dene/mamma mia/Mamma Mia-En.srt
SUB: Detected subtitle file format: subviewer
SUB: Read 1249 subtitles.
SUB: Adjusted 79 subtitle(s).
ID_FILE_SUB_ID=1
ID_FILE_SUB_FILENAME=/media/Yerel Disk 250/dene/mamma mia/Mamma Mia-Tr.srt
SUB: Added subtitle file (2): /media/Yerel Disk 250/dene/mamma mia/Mamma Mia-Tr.srt
ID_FILENAME=/media/Yerel Disk 250/dene/mamma mia/Mamma Mia.avi
ID_DEMUXER=avi
ID_VIDEO_FORMAT=XVID
ID_VIDEO_BITRATE=795752
ID_VIDEO_WIDTH=640
ID_VIDEO_HEIGHT=272
ID_VIDEO_FPS=25.000
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=85
ID_AUDIO_BITRATE=126568
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_LENGTH=6251.64
[***] auto-open
Opening video filter: [hue]
Opening video filter: [eq2]
Opening video filter: [screenshot]
Opening video filter: [harddup]
Opening video filter: [expand aspect=1.33333]
Expand: -1 x -1, -1 ; -1, osd: 0, aspect: 1.333330, round: 1
[***] Init
[***] Updating font cache.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
ID_VIDEO_CODEC=ffodivx
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
ID_AUDIO_CODEC=mad
Starting playback...
VDec: vo config request - 640 x 272 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.35:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=2.3529
[swscaler @ 0x89662f0]SwScaler: using unscaled yuv420p -> bgr24 special converter
VO: [x11] 640x480 => 640x480 Planar YV12  [zoom]
X11 error: BadAccess during XSelectInput Call
X11 error: The 'ButtonPressMask' mask of specified window has probably already used by another appication (see man XSelectInput)
X11 error: MPlayer discards mouse control (reconfiguring)
X11 error: BadAccess during XSelectInput Call
X11 error: The 'ButtonPressMask' mask of specified window has probably already used by another appication (see man XSelectInput)
X11 error: MPlayer discards mouse control (reconfiguring)
[AO_ALSA] Unable to find simple control 'PCM',0.
[Mixer] No hardware mixing, inserting volume filter.
[AO_ALSA] Unable to find simple control 'PCM',0.
[***] PlayResX undefined, setting 384.
[***] fontconfig: Selected font family is not the requested one: 'DejaVu Sans' != 'Sans'
[***] Glyph 0x92 not found, reselecting font for (Sans, 200, 0)
[***] fontconfig_select: Using default font: (Sans, 200, 0) -> /home/hatalar205/.mplayer/subfont.ttf, 0
[***] Error opening font: /home/hatalar205/.mplayer/subfont.ttf, 0


MPlayer interrupted by signal 11 in module: filter_video
ID_SIGNAL=11
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

---

### Post by rvm4000 on 2009-01-17
> **hatalar205 said:**
> [***] fontconfig: Selected font family is not the requested one: 'DejaVu Sans' != 'Sans'
[***] Glyph 0x92 not found, reselecting font for (Sans, 200, 0)
[***] fontconfig_select: Using default font: (Sans, 200, 0) -> /home/hatalar205/.mplayer/subfont.ttf, 0
[***] Error opening font: /home/hatalar205/.mplayer/subfont.ttf, 0

This looks like an old bug in mplayer 1.0rc2 fixed a lot of time ago, which made it crash when it couldn't find a character for the subtitles (although I don't know how this problem makes your screen black, maybe a bug in the driver of your graphic card?).

You can find a newer version of mplayer here:
[https://launchpad.net/~rvm/+archive](https://launchpad.net/~rvm/+archive)

---

### Post by hatalar205 on 2009-01-19
I have done what you said. And eveything is OK. Thanks a lot for your kind help.

---

### Post by Giga777 on 2009-03-04
deleted

---

