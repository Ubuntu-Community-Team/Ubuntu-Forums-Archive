---
title: "Cannot play DVD or Music, I do not think this is a 'sound' problem"
date: 2009-01-18
forum: Multimedia Software
---

### Post by skr on 2009-01-18
I cannot play Music or DVD's.

Ubuntu 8.10  Gnome
HP2133 Mininote - bought to take with me when travelling to surf and have access to music and films :(

I 'think' I have all the correct codecs installed.


_**Music**_
Open a mp3 or ogg file with Rythumbox and it indicates that it playing but the timer does not move from '00:00 of 3:27'.  I can pause it and it says Paused and then I click play but nothing.
[B][U]
DVDs[/U][/B]
I have tried various applications and most have the same result as playing music, they will not play.  Some DVDs start and I see the inital copy right warning and the times sits at '00:00 of 00:10'.  
By tring to browser to a different chapter I get Smplayer to crash, the log file is:
/usr/bin/mplayer -noquiet -nofs -sub-fuzziness 1 -identify -slave -vo x11 -ao pulse -zoom -nokeepaspect -framedrop -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 56623116 -monitorpixelaspect 1 -subfont-autoscale 1 -subfont-text-scale 5 -subcp ISO-8859-1 -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -dvd-device /media/cdrom0 -dvdangle 1 -nocache -osdlevel 0 -vf-add screenshot -channels 2 dvd://1

MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: VIA C7-M Processor 1200MHz (Family: 6, Model: 13, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing dvd://1.
ID_DVD_TITLES=8
ID_DVD_TITLE_1_CHAPTERS=2
ID_DVD_TITLE_1_ANGLES=1
ID_DVD_TITLE_2_CHAPTERS=3
ID_DVD_TITLE_2_ANGLES=1
ID_DVD_TITLE_3_CHAPTERS=1
ID_DVD_TITLE_3_ANGLES=1
ID_DVD_TITLE_4_CHAPTERS=1
ID_DVD_TITLE_4_ANGLES=1
ID_DVD_TITLE_5_CHAPTERS=1
ID_DVD_TITLE_5_ANGLES=1
ID_DVD_TITLE_6_CHAPTERS=1
ID_DVD_TITLE_6_ANGLES=1
ID_DVD_TITLE_7_CHAPTERS=1
ID_DVD_TITLE_7_ANGLES=1
ID_DVD_TITLE_8_CHAPTERS=1
ID_DVD_TITLE_8_ANGLES=1
ID_DVD_TITLE_1_LENGTH=10.000
ID_DVD_TITLE_2_LENGTH=8166.520
ID_DVD_TITLE_3_LENGTH=115.960
ID_DVD_TITLE_4_LENGTH=127.000
ID_DVD_TITLE_5_LENGTH=93.960
ID_DVD_TITLE_6_LENGTH=146.000
ID_DVD_TITLE_7_LENGTH=145.920
ID_DVD_TITLE_8_LENGTH=133.080
ID_DVD_DISC_ID=04C98DF364C109062A742AA615251F2D
There are 8 titles on this DVD.
ID_DVD_CURRENT_TITLE=1
There are 2 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (stereo) language: en aid: 128.
ID_AUDIO_ID=128
ID_AID_128_LANG=en
number of audio channels on disk: 1.
number of subtitles on disk: 0
CHAPTERS: 00:00:00,00:00:05,
ID_VIDEO_ID=0
MPEG-PS file format detected.
ID_AUDIO_ID=128
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  8000.0 kbps (1000.0 kbyte/s)
ID_FILENAME=dvd://1
ID_DEMUXER=mpegps
ID_VIDEO_FORMAT=0x10000002
ID_VIDEO_BITRATE=8000000
ID_VIDEO_WIDTH=720
ID_VIDEO_HEIGHT=576
ID_VIDEO_FPS=25.000
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=8192
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_LENGTH=10.00
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
Opening video filter: [screenshot]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :
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
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=1.7778
SwScaler: reducing / aligning filtersize 5 -> 4
SwScaler: reducing / aligning filtersize 5 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 5 -> 4
[swscaler @ 0x89662f0]SwScaler: BICUBIC scaler, from yuv420p to bgr24 using MMX2
[swscaler @ 0x89662f0]SwScaler: using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0x89662f0]SwScaler: using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0x89662f0]SwScaler: using n-tap MMX scaler for vertical scaling (BGR)
[swscaler @ 0x89662f0]SwScaler: using MMX2 YV12->BGR24 Converter
[swscaler @ 0x89662f0]SwScaler: 720x576 -> 1024x576
VO: [x11] 720x576 => 1024x576 Planar YV12  [zoom]
X11 error: BadAccess during XSelectInput Call
X11 error: The 'ButtonPressMask' mask of specified window has probably already used by another appication (see man XSelectInput)
X11 error: MPlayer discards mouse control (reconfiguring)
X11 error: BadAccess during XSelectInput Call
X11 error: The 'ButtonPressMask' mask of specified window has probably already used by another appication (see man XSelectInput)
X11 error: MPlayer discards mouse control (reconfiguring)
ID_AUDIO_TRACK=128

GNOME screensaver enabled


Many thanks if anyone could assist.

---

### Post by cariboo on 2009-01-18
I would suggest you install the ubuntu-restricted-extras meta package, to make sure you have all the codecs you need to play most types of media. 

For DVD playback it looks like you need libdvdcss2 which is available in the Medibutu repositories. To enable the Medibuntu repositories go [here]("http://help.ubuntu.com/community/Medibuntu") and follow the instructions.

Once you have updated the repositories, you can use Synaptic Package Manager to install the ubuntu-restricted-extras and libdvdcss2 packages.

Jim

---

### Post by skr on 2009-01-19
Thanks but that was the first thing I did before raising this question.  I have checked and version 25 of ubuntu-restricted-extras is the latest and installed version

---

