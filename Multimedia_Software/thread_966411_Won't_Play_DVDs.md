---
title: "Won't Play DVDs"
date: 2008-11-01
forum: Multimedia Software
---

### Post by kshsj777 on 2008-11-01
I just got an MSI Wind a few days ago and this is the first time I tried to play a DVD using a USB DVD drive.  I tried VLC first, changing the default directory to /media/cdrom0 but it refuses to play anything.

Totem will play the first few seconds of the dvd and then says "could not read from resource"

SMPlayer crashes, and gives me this log:

/usr/bin/mplayer -noquiet -nofs -sub-fuzziness 1 -identify -slave -vo xv, -zoom -nokeepaspect -framedrop -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 58720268 -monitorpixelaspect 1 -subfont-autoscale 1 -subfont-text-scale 5 -subcp ISO-8859-1 -subcc -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -dvd-device /media/cdrom -dvdangle 1 -nocache -osdlevel 0 -vf-add screenshot -channels 2 dvd://1

MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Atom(TM) CPU N270   @ 1.60GHz (Family: 6, Model: 28, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing dvd://1.
ID_DVD_TITLES=12
ID_DVD_TITLE_1_CHAPTERS=28
ID_DVD_TITLE_1_ANGLES=1
ID_DVD_TITLE_2_CHAPTERS=2
ID_DVD_TITLE_2_ANGLES=1
ID_DVD_TITLE_3_CHAPTERS=5
ID_DVD_TITLE_3_ANGLES=1
ID_DVD_TITLE_4_CHAPTERS=2
ID_DVD_TITLE_4_ANGLES=1
ID_DVD_TITLE_5_CHAPTERS=89
ID_DVD_TITLE_5_ANGLES=1
ID_DVD_TITLE_6_CHAPTERS=11
ID_DVD_TITLE_6_ANGLES=1
ID_DVD_TITLE_7_CHAPTERS=2
ID_DVD_TITLE_7_ANGLES=1
ID_DVD_TITLE_8_CHAPTERS=2
ID_DVD_TITLE_8_ANGLES=1
ID_DVD_TITLE_9_CHAPTERS=2
ID_DVD_TITLE_9_ANGLES=1
ID_DVD_TITLE_10_CHAPTERS=2
ID_DVD_TITLE_10_ANGLES=1
ID_DVD_TITLE_11_CHAPTERS=2
ID_DVD_TITLE_11_ANGLES=1
ID_DVD_TITLE_12_CHAPTERS=1
ID_DVD_TITLE_12_ANGLES=1
ID_DVD_TITLE_12_LENGTH=0.500
ID_DVD_TITLE_7_LENGTH=9.333
ID_DVD_TITLE_8_LENGTH=9.333
ID_DVD_TITLE_11_LENGTH=9.834
ID_DVD_TITLE_10_LENGTH=9.834
*** Zero check failed in ifo_read.c:1060
    for vts_ptt_srpt->zero_1 = 0x57b6
*** Zero check failed in ifo_read.c:1535
    for c_adt->zero_1 = 0xc834
libdvdread: Invalid title IFO (VTS_06_0.IFO).
ID_DVD_TITLE_9_LENGTH=0.500
ID_DVD_TITLE_2_LENGTH=235.300
ID_DVD_TITLE_1_LENGTH=5895.200
ID_DVD_TITLE_4_LENGTH=1636.333
ID_DVD_TITLE_3_LENGTH=153.300
ID_DVD_TITLE_5_LENGTH=3.500
ID_DVD_TITLE_6_LENGTH=0.500
There are 12 titles on this DVD.
ID_DVD_CURRENT_TITLE=1
There are 28 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
ID_AUDIO_ID=128
ID_AID_128_LANG=en
audio stream: 1 format: ac3 (stereo) language: es aid: 129.
ID_AUDIO_ID=129
ID_AID_129_LANG=es
audio stream: 2 format: ac3 (stereo) language: en aid: 130.
ID_AUDIO_ID=130
ID_AID_130_LANG=en
audio stream: 3 format: ac3 (stereo) language: en aid: 131.
ID_AUDIO_ID=131
ID_AID_131_LANG=en
number of audio channels on disk: 4.
subtitle ( sid ): 3 language: en
ID_SUBTITLE_ID=3
ID_SID_3_LANG=en
subtitle ( sid ): 4 language: fr
ID_SUBTITLE_ID=4
ID_SID_4_LANG=fr
subtitle ( sid ): 5 language: es
ID_SUBTITLE_ID=5
ID_SID_5_LANG=es
number of subtitles on disk: 3
CHAPTERS: 00:00:00,00:02:14,00:05:42,00:07:24,00:10:00,00:13:23,00:19:06,00:25:03,00:29:27,00:34:54,00:40:29,00:45:28,00:48:06,00:50:22,00:52:06,00:54:42,00:57:22,01:00:28,01:03:41,01:06:56,01:10:03,01:14:28,01:17:46,01:20:57,01:24:30,01:25:25,01:27:20,01:33:33,
ID_VIDEO_ID=0
MPEG-PS file format detected.
ID_AUDIO_ID=130
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  9800.0 kbps (1225.0 kbyte/s)
ID_FILENAME=dvd://1
ID_DEMUXER=mpegps
ID_VIDEO_FORMAT=0x10000002
ID_VIDEO_BITRATE=9800000
ID_VIDEO_WIDTH=720
ID_VIDEO_HEIGHT=480
ID_VIDEO_FPS=29.970
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=8192
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_LENGTH=5895.20
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
Opening video filter: [screenshot]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
ID_VIDEO_CODEC=mpeg12
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
ID_AUDIO_BITRATE=192000
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
ID_AUDIO_CODEC=a52
Starting playback...
ID_AUDIO_ID=128
ID_AUDIO_ID=131
ID_AUDIO_ID=129
a52: CRC check failed!  
a52: error at resampling
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=1.7778
SwScaler: reducing / aligning filtersize 5 -> 4
SwScaler: reducing / aligning filtersize 5 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 5 -> 4
[swscaler @ 0x89652b0]SwScaler: BICUBIC scaler, from yuv420p to bgr24 using MMX2
[swscaler @ 0x89652b0]SwScaler: using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0x89652b0]SwScaler: using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0x89652b0]SwScaler: using n-tap MMX scaler for vertical scaling (BGR)
[swscaler @ 0x89652b0]SwScaler: using MMX2 YV12->BGR24 Converter
[swscaler @ 0x89652b0]SwScaler: 720x480 -> 854x480
VO: [xv] 720x480 => 854x480 Planar YV12  [zoom]
X11 error: BadAccess during XSelectInput Call
X11 error: The 'ButtonPressMask' mask of specified window has probably already used by another appication (see man XSelectInput)
X11 error: MPlayer discards mouse control (reconfiguring)

_______________________

Any ideas why?  Is it the fact it's a usb drive, a software issue, or what?
Thanks
777

---

### Post by kshsj777 on 2008-11-01
Nevermind.  I didn't have libdvdcss2 installed.

---

### Post by lukjad on 2008-11-01
Happens to the best of us. Please mark this thread as solved. :D

---

### Post by archie1941 on 2010-11-11
I also had the missing lib so thanks from the newbie:)

---

### Post by archie1941 on 2010-11-11
> **kshsj777 said:**
> Nevermind.  I didn't have libdvdcss2 installed.
I didn't even know I was missing anything. Thanks for your post it saved the day.
[email]k8fa.art@gmail.com[/email]:):)

---

