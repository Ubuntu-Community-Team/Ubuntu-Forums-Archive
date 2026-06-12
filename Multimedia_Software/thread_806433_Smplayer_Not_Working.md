---
title: "Smplayer Not Working"
date: 2008-05-24
forum: Multimedia Software
---

### Post by Jenga-kun on 2008-05-24
I am currently running Hardy Heron and I'm trying to get smplayer to work. It's supposed to work out of the box with most of my stuff but whenever I use it I either get no video and no sound, or sound but no video. I've tried installing some codecs and I've installed the essential packages from here: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) but I still have the same problem.

---

### Post by rvm4000 on 2008-05-25
What does the mplayer log say (Options->View logs) when you try to play one of those files?

---

### Post by Jenga-kun on 2008-05-25
Mplayer says this:

/usr/bin/mplayer -noquiet -nofs -sub-fuzziness 1 -identify -msglevel demux=6 -slave -vo xv -ao alsa -zoom -nokeepaspect -framedrop -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 44040204 -colorkey 0x020202 -monitoraspect 1.6 -*** -embeddedfonts -***-color ffff0000 -***-border-color 00000000 -subfont-autoscale 1 -***-font-scale 1 -subcp ISO-8859-1 -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -nocache -osdlevel 0 -vf-add screenshot -channels 2 /media/disk/Videos/[Eclipse] Code Geass - Lelouch of the Rebellion R2 - 02 (1280x720 h264) [98828FD5].mkv

MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 47, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing /media/disk/Videos/[Eclipse] Code Geass - Lelouch of the Rebellion R2 - 02 (1280x720 h264) [98828FD5].mkv.
Checking for YUV4MPEG2
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
[mkv] Found the head...
[mkv] + a segment...
[mkv] /---- [ parsing seek head ] ---------
[mkv] /---- [ parsing seek head ] ---------
[mkv] \---- [ parsing seek head ] ---------
[mkv] /---- [ parsing cues ] -----------
[mkv] \---- [ parsing cues ] -----------
[mkv] /---- [ parsing chapters ] ---------
[mkv] Chapter 0 from 00:00:00.000 to 00:00:00.000, Prologue
[mkv] Chapter 1 from 00:00:33.100 to 00:00:00.000, Opening
[mkv] Chapter 2 from 00:02:03.000 to 00:00:00.000, Code Geass R2 - 02: Japan Independence Plan
[mkv] Chapter 3 from 00:22:02.500 to 00:00:00.000, Ending
[mkv] Chapter 4 from 00:23:35.000 to 00:00:00.000, Preview
[mkv] \---- [ parsing chapters ] ---------
[mkv] \---- [ parsing seek head ] ---------
[mkv] |+ segment information...
[mkv] | + timecode scale: 1000000
[mkv] | + duration: 1430.013s
[mkv] |+ segment tracks...
[mkv] | + a track...
[mkv] |  + Track number: 1
[mkv] |  + Track type: Video
[mkv] |  + Default flag: 1
[mkv] |  + Codec ID: V_MPEG4/ISO/AVC
[mkv] |  + CodecPrivate, length 39
[mkv] |  + Default duration: 41.708ms ( = 23.976 fps)
[mkv] |  + Language: eng
[mkv] |  + Name: Code Geass R2 - 02: Japan Independence Plan
[mkv] |  + Video track
[mkv] |   + Pixel width: 1280
[mkv] |   + Pixel height: 720
[mkv] |   + Display width: 16
[mkv] |   + Display height: 9
[mkv] | + a track...
[mkv] |  + Track number: 2
[mkv] |  + Track type: Audio
[mkv] |  + Default flag: 1
[mkv] |  + Codec ID: A_VORBIS
[mkv] |  + CodecPrivate, length 4245
[mkv] |  + Language: jpn
[mkv] |  + Name: 2.0 Vorbis
[mkv] |  + Audio track
[mkv] |   + Sampling frequency: 48000.000000
[mkv] |   + Channels: 2
[mkv] | + a track...
[mkv] |  + Track number: 3
[mkv] |  + Track type: Subtitle
[mkv] |  + Default flag: 1
[mkv] |  + Codec ID: S_TEXT/***
[mkv] |  + CodecPrivate, length 1646
[mkv] |  + Language: eng
[mkv] |  + Name: ***
[mkv] | + a track...
[mkv] |  + Track number: 4
[mkv] |  + Track type: Subtitle
[mkv] |  + Default flag: 0
[mkv] |  + Codec ID: S_TEXT/UTF8
[mkv] |  + Language: eng
[mkv] |  + Name: SRT
[mkv] /---- [ parsing attachments ] ---------
[mkv] | + an attachment...
[mkv] |  + FileName: ClearfaceGothic Regular.ttf
[mkv] |  + FileMimeType: application/x-truetype-font
[mkv] |  + FileData, length 57856
[mkv] Attachment: ClearfaceGothic Regular.ttf, application/x-truetype-font, 57856 bytes
[mkv] | + an attachment...
[mkv] |  + FileName: AVGARDNEclipse.ttf
[mkv] |  + FileMimeType: application/x-truetype-font
[mkv] |  + FileData, length 56924
[mkv] Attachment: AVGARDNEclipse.ttf, application/x-truetype-font, 56924 bytes
[mkv] | + an attachment...
[mkv] |  + FileName: ClearfaceGothic Bold Italic.ttf
[mkv] |  + FileMimeType: application/x-truetype-font
[mkv] |  + FileData, length 54696
[mkv] Attachment: ClearfaceGothic Bold Italic.ttf, application/x-truetype-font, 54696 bytes
[mkv] | + an attachment...
[mkv] |  + FileName: ClearfaceGothic Bold.ttf
[mkv] |  + FileMimeType: application/x-truetype-font
[mkv] |  + FileData, length 57032
[mkv] Attachment: ClearfaceGothic Bold.ttf, application/x-truetype-font, 57032 bytes
[mkv] | + an attachment...
[mkv] |  + FileName: ClearfaceGothic Italic.ttf
[mkv] |  + FileMimeType: application/x-truetype-font
[mkv] |  + FileData, length 57104
[mkv] Attachment: ClearfaceGothic Italic.ttf, application/x-truetype-font, 57104 bytes
[mkv] \---- [ parsing attachments ] ---------
[mkv] |+ found cluster, headers are parsed completely :)
ID_VIDEO_ID=0
[mkv] Aspect: 1.777778
ID_VID_0_NAME=Code Geass R2 - 02: Japan Independence Plan
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "Code Geass R2 - 02: Japan Independence Plan", -vid 0
ID_AUDIO_ID=0
ID_AID_0_NAME=2.0 Vorbis
ID_AID_0_LANG=jpn
[mkv] Track ID 2: audio (A_VORBIS) "2.0 Vorbis", -aid 0, -alang jpn
ID_SUBTITLE_ID=0
ID_SID_0_NAME=***
ID_SID_0_LANG=eng
[mkv] Track ID 3: subtitles (S_TEXT/***) "***", -sid 0, -slang eng
ID_SUBTITLE_ID=1
ID_SID_1_NAME=SRT
ID_SID_1_LANG=eng
[mkv] Track ID 4: subtitles (S_TEXT/UTF8) "SRT", -sid 1, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1280x720  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
ID_FILENAME=/media/disk/Videos/[Eclipse] Code Geass - Lelouch of the Rebellion R2 - 02 (1280x720 h264) [98828FD5].mkv
ID_DEMUXER=mkv
ID_VIDEO_FORMAT=avc1
ID_VIDEO_BITRATE=0
ID_VIDEO_WIDTH=1280
ID_VIDEO_HEIGHT=720
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=1.7778
ID_AUDIO_FORMAT=vrbs
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
ID_LENGTH=1430.01
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 0.0 kbit/0.00% (ratio: 0->192000)
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis decoder)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
ID_AUDIO_CODEC=ffvorbis
Video: no video
Starting playback...
ID_AUDIO_TRACK=0

---

### Post by Jenga-kun on 2008-05-25
Can somebody please help?

---

### Post by rvm4000 on 2008-05-25
> **Jenga-kun said:**
> 
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
Error opening/initializing the selected video_out (-vo) device.


For some reason xv doesn't work for you. 
Go to Preferences->General and select x11 (or gl or gl2) as video output driver instead.

---

