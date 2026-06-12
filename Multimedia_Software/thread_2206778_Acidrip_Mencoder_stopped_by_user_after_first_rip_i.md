---
title: "Acidrip: Mencoder stopped by user after first rip in queue"
date: 2014-02-20
forum: Multimedia Software
---

### Post by michele5 on 2014-02-20
I'm trying to rip each chapter of a DVD separately. Every chapter is put in the queue but Acidrip stops after correctly ripping the first chapter with the message "Mencoder stopped by user"
I tried installing css (sudo /usr/share/doc/libdvdread4/install-css.sh) but still doesn't work.

Any idea?
Note: to read the DVD player I had to change the path from /dev/dvd to /dev/cdrom

Here is the first and the last part of the debug (I've set 2 chapters called "heidi_14_OperazioneFioccoDiNeve" and "heidi_15_VittoriaSudata"

AcidRip message - title has been set to heidi_14_OperazioneFioccoDiNeve
AcidRip message - Selected_subp changed to -1
AcidRip message - more_options has been set to heidi_14_OperazioneFioccoDiNeve
AcidRip message - Selected_subp changed to 1
AcidRip message - Pushed events onto queue
AcidRip message - title has been set to heidi_15_VittoriaSudata
AcidRip message - Selected_subp changed to -1
AcidRip message - more_options has been set to heidi_15_VittoriaSudata
AcidRip message - Selected_subp changed to 1
AcidRip message - Pushed events onto queue
AcidRip message - Playlist contains 4 item(s)
AcidRip message - Running unlink frameno.avi 2> /dev/null
AcidRip message - Removing frameno.avi if it exists
AcidRip message - Running mencoder dvd://1 -dvd-device /dev/cdrom -chapter 4-4 -alang English -sid 0 -vobsubout /home/michele/heidi_14_OperazioneFioccoDiNeve -info srcform="DVD ripped by acidrip.sf.net" -oac mp3lame -lameopts abr:br=128  -ovc lavc -lavcopts vcodec=mpeg4:vhq:v4mv:vqmin=2:vbitrate=689 -vf pp=de,crop=0:0:0:0,scale=480:-2   heidi_14_OperazioneFioccoDiNeve -o "/home/michele/heidi_14_OperazioneFioccoDiNeve.avi"
AcidRip message - Encoding film
MEncoder svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team
libdvdread: Using libdvdcss version 1.2.13 for DVD access
There are 1 titles on this DVD.
There are 1 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000124
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00001e87
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000076fe
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
audio stream: 0 format: ac3 (stereo) language: it aid: 128.
audio stream: 1 format: ac3 (stereo) language: ja aid: 129.
number of audio channels on disk: 2.
subtitle ( sid ): 0 language: it
number of subtitles on disk: 1

success: format: 2  data: 0x0 - 0x4cd9a800
No matching DVD audio language found!
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  8500.0 kbps (1062.5 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x576  fps:25.000  ftime:=0.0400
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [scale w=480 h=-2]
Opening video filter: [crop w=0 h=0 x=0 y=0]
Crop: 0 x 0, 0 ; 0
Opening video filter: [pp=de]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
MP3 audio selected.
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Unsupported PixelFormat 81
[PP] Using external postprocessing filter, max q = 6.
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
[swscaler @ 0xb6d351c0]BICUBIC scaler, from yuv420p to yuv420p using MMX2
videocodec: libavcodec (480x360 fourcc=34504d46 [FMP4])
[VE_LAVC] High quality encoding selected (non-realtime)!
Pos:   0.0s      1f (299%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]

Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.0s      2f (299%)  0.00fps Trem:   0min   0mb  A-V:0.004 [0:0]


[...]


File not found: 'heidi_14_OperazioneFioccoDiNeve'
Failed to open heidi_14_OperazioneFioccoDiNeve.
Cannot open file/device.

Exiting...
AcidRip message - Clearing 2 remaining playlist items
AcidRip message - Mencoder interrupted by user

---

