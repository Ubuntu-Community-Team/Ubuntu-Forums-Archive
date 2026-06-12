---
title: "OGMrip error"
date: 2010-10-23
forum: Multimedia Software
---

### Post by idstealth on 2010-10-23
Hi guys, I've recently gotten an Ipod Touch and am trying to convert my DVDs for the Ipod Touch. I am using OGMrip. However, everytime I try to convert, I get an error and the conversion fails. Anyone know why? I have tried many other programs, but OGMrip looks the most promising. Anyway, here's the log file.

[HTML]ENCODING: The Naked Gun


Profile: /apps/ogmrip/profiles/default-iphone
--------

audio/channels = 1
audio/codec = aac
audio/normalize = true
audio/quality = 3
audio/srate = 0
container/ensure_sync = true
container/format = mp4
container/fourcc = 0
container/target_number = 1
container/target_size = 700
subp/charset = 0
subp/codec = srt
subp/forced = false
subp/newline = 0
subp/spell_check = false
version = 1.1
video/bitrate = 1500
video/codec = x264
video/deblock = false
video/denoise = true
video/dering = false
video/encoding = 1
video/expand = true
video/max_height = 480
video/max_width = 640
video/passes = 2
video/preset = 3
video/qpel = false
video/quantizer = 3.000000
video/scaler = 7
video/trellis = true
video/turbo = true
x264/b_adapt = 2
x264/b_pyramid = 2
x264/bframes = 0
x264/cabac = false
x264/dct8x8 = false
x264/frameref = 5
x264/level_idc = 30
x264/me = 3
x264/mixed_refs = true
x264/profile = 0
x264/rc_lookahead = 50
x264/subq = 8
x264/vbv_bufsize = 10000
x264/vbv_maxrate = 10000
x264/weight_b = true
x264/weight_p = 0


Analyzing video title 1
-----------------------

mplayer -nolirc -nosound -nocache -noconfig all -v -benchmark -vo null -vf pullup -dvdangle 1 -frames 500 -dvd-device /media/NAKED_GUN dvd://1 
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device /dev/sr0 mounted on /media/NAKED_GUN for CSS authentication

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000122
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001ec
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000004b4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001fc19b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001fc19f
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
Unsupported PixelFormat -1
[mpeg1video @ 0x9c33f10]removing common factors from framerate
[mpeg2video @ 0x9c34500]ac-tex damaged at 34 6
[mpeg2video @ 0x9c34500]Warning MVs not available
[mpeg2video @ 0x9c34500]concealing 1080 DC, 1080 AC, 1080 MV errors
Warning! FPS changed 23.976 -> 29.970  (-5.994005) [4]  
Warning! FPS changed 23.976 -> 29.970  (-5.994005) [4]  

Telecine: true
Progressive: true


Encoding audio stream 01
------------------------

mplayer -nolirc -nocache -noframedrop -noconfig all -vc dummy -vo null -ao pcm:waveheader:file=/tmp/fifo.9XSBLV -format s16le -af volnorm=1 -channels 2 -aid 128 -dvd-device /media/NAKED_GUN dvd://1 
faac -q 157 --mpeg-vers 4 -o /tmp/audio.CUSBLV /tmp/fifo.9XSBLV 
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device /dev/sr0 mounted on /media/NAKED_GUN for CSS authentication
Freeware Advanced Audio Coder
FAAC 1.26.1 (Aug 16 2008) UNSTABLE


libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000122
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001ec
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000004b4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001fc19b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001fc19f
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
Cannot find codec matching selected -vo and video format 0x10000002.
Using SSE optimized IMDCT transform
Using MMX optimized resampler
Quantization quality: 157
Bandwidth: 22840 Hz
Object type: Low Complexity(MPEG-4) + M/S
Container format: Transport Stream (ADTS)
Encoding /tmp/fifo.9XSBLV to /tmp/audio.CUSBLV
   frame          | bitrate | elapsed/estim | play/CPU | ETA
131/524288 (  0%)|   67.5  |    0.1/400.2  |   27.94x | 400.1 
  132/524288 (  0%)|   68.2  |    0.1/397.2  |   28.16x | 397.1 
  133/524288 (  0%)|   69.0  |    0.1/394.2  |   28.37x | 394.1 
  150/524288 (  0%)|   80.2  |    0.1/419.5  |   26.67x | 419.3 
  200/524288 (  0%)|  102.6  |    0.2/450.9  |   24.80x | 450.7 
  250/524288 (  0%)|  117.2  |    0.2/478.2  |   23.39x | 478.0 
  300/524288 (  0%)|  127.4  |    0.3/496.4  |   22.53x | 496.1 
  350/524288 (  0%)|  133.7  |    0.3/509.3  |   21.96x | 509.0 
  400/524288 (  0%)|  139.0  |    0.4/524.3  |   21.33x | 523.9 
  450/524288 (  0%)|  145.7  |    0.5/531.3  |   21.05x | 530.9 
  500/524288 (  0%)|  157.9  |    0.5/541.1  |   20.67x | 540.6 
  550/524288 (  0%)|  163.8  |    0.6/545.3  |   20.51x | 544.7 
  600/524288 (  0%)|  164.8  |    0.6/548.8  |   20.38x | 548.2 
  650/524288 (  0%)|  165.4  |    0.7/548.5  |   20.39x | 547.8 
   and it goes on until.....
238800/524288 ( 45%)|  202.7  |  260.9/572.8  |   19.53x | 311.9 
238850/524288 ( 45%)|  202.6  |  260.9/572.6  |   19.53x | 311.8 
238900/524288 ( 45%)|  202.6  |  260.9/572.5  |   19.54x | 311.6 
238950/524288 ( 45%)|  202.5  |  260.9/572.4  |   19.54x | 311.5 
239000/524288 ( 45%)|  202.5  |  260.9/572.3  |   19.54x | 311.4 
239050/524288 ( 45%)|  202.5  |  260.9/572.2  |   19.55x | 311.3 
239100/524288 ( 45%)|  202.4  |  260.9/572.0  |   19.55x | 311.2 Could not seek to start, WAV size headers not updated!

239137/524288 ( 45%)|  202.4  |  260.9/571.9  |   19.56x | 311.1 


Setting video parameters
------------------------
Constant bitrate: 1500000 bps

mplayer -nolirc -vo null -nosound -nocache -noconfig all -speed 100 -dvdangle 1 -vf cropdetect -ss 1019 -frames 12 -dvd-device /media/NAKED_GUN dvd://1 
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device /dev/sr0 mounted on /media/NAKED_GUN for CSS authentication

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000122
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001ec
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000004b4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001fc19b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001fc19f
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
Unsupported PixelFormat -1
[mpeg1video @ 0xa267ea0]removing common factors from framerate
mplayer -nolirc -vo null -nosound -nocache -noconfig all -speed 100 -dvdangle 1 -vf cropdetect -ss 2039 -frames 12 -dvd-device /media/NAKED_GUN dvd://1 
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device /dev/sr0 mounted on /media/NAKED_GUN for CSS authentication

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000122
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001ec
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000004b4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001fc19b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001fc19f
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
Unsupported PixelFormat -1
[mpeg1video @ 0x9e85ea0]removing common factors from framerate
mplayer -nolirc -vo null -nosound -nocache -noconfig all -speed 100 -dvdangle 1 -vf cropdetect -ss 3058 -frames 12 -dvd-device /media/NAKED_GUN dvd://1 
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device /dev/sr0 mounted on /media/NAKED_GUN for CSS authentication

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000122
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001ec
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000004b4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001fc19b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001fc19f
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
Unsupported PixelFormat -1
[mpeg1video @ 0x9583ea0]removing common factors from framerate
mplayer -nolirc -vo null -nosound -nocache -noconfig all -speed 100 -dvdangle 1 -vf cropdetect -ss 4077 -frames 12 -dvd-device /media/NAKED_GUN dvd://1 
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device /dev/sr0 mounted on /media/NAKED_GUN for CSS authentication

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000122
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001ec
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000004b4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001fc19b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001fc19f
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
Unsupported PixelFormat -1
[mpeg1video @ 0x8bacea0]removing common factors from framerate
mplayer -nolirc -vo null -nosound -nocache -noconfig all -speed 100 -dvdangle 1 -vf cropdetect -ss 5096 -frames 12 -dvd-device /media/NAKED_GUN dvd://1 
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device /dev/sr0 mounted on /media/NAKED_GUN for CSS authentication

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000122
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001ec
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000004b4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001fc19b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001fc19f
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
Unsupported PixelFormat -1
[mpeg1video @ 0x86ccea0]removing common factors from framerate

Automatic cropping: 8,0 704x480

Automatic scaling: 640x369

TESTING: The Naked Gun

mencoder -nocache -noslices -noconfig all -oac pcm -srate 8000 -af channels=1,lavcresample=8000 -aid 128 -spuaa 20 -sid 0 -forcedsubsonly -sws 7 -vf pullup,softskip,crop=704:480:8:0,scale=5:3,expand=640:480,hqdn3d=2:1:2,harddup -ofps 24000/1001 -zoom -frames 15 -dvdangle 1 -o /tmp/video.TYL7KV -dvd-device /media/NAKED_GUN -ovc x264 -x264encopts deblock=-1,-1:subq=7:direct_pred=auto:frameref=3:b_adapt=1:me=hex:merange=16:rc_lookahead=40:bframes=3:trellis=1:keyint=250:cqm=flat:weight_b:noglobal_header:cabac:weightp=2:8x8dct:mixed_refs:level_idc=51:b_pyramid=normal:partitions=all:psy-rd=1.00,0.15:crf=18:threads=4 dvd://1 
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device /dev/sr0 mounted on /media/NAKED_GUN for CSS authentication

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000122
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001ec
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000004b4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001fc19b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001fc19f
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
Using SSE optimized IMDCT transform
Using MMX optimized resampler
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
Unsupported PixelFormat -1
swScaler: 704x480 -> 6x4 is invalid scaling dimension
Couldn't init SwScaler for this setup
FATAL: Cannot initialize video driver.
[mpeg2video @ 0x140fac0]ac-tex damaged at 34 6
[mpeg2video @ 0x140fac0]Warning MVs not available
 
[/HTML]

And yes, I like the Naked Gun, but only the first film. (:

---

### Post by bluekarasu on 2010-10-23
Try Handbrake, with the built in ipod profile.

---

### Post by idstealth on 2010-10-23
Handbrake can't handle encrypted DVDs and requires other DVD rippers to get the VIDEO_TS folders and .VOB files first. I've not had much luck with DVD rippers too, especially with dvd::rip because it can't seem to rip multiple .VOB files to the same output file. (This is useful as some movies have individual .VOB files for each chapter). Any recommendations?

---

### Post by bluekarasu on 2010-10-23
to rip/decrypt, use Vobcopy
It's a command line tool, but very simple :

```
cd the-folder-you-want-your-video_ts
vobcopy -m
```

And you'll get a full copy of your DVD, handbrake will love it.

---

### Post by idstealth on 2010-10-23
CLI Happiness. :D Thanks!

---

### Post by JohnAStebbins on 2010-10-23
> **idstealth said:**
> Handbrake can't handle encrypted DVDs and requires other DVD rippers to get the VIDEO_TS folders and .VOB files first. I've not had much luck with DVD rippers too, especially with dvd::rip because it can't seem to rip multiple .VOB files to the same output file. (This is useful as some movies have individual .VOB files for each chapter). Any recommendations?
Not true.  Just install libdvdcss.
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

