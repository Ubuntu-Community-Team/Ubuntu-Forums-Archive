---
title: "Can't get vdpau to work in Lucid."
date: 2010-05-01
forum: Multimedia Software
---

### Post by Shibblet on 2010-05-01
SMplayer has a vdpau option, turn it on, and it stops playing video.  XV works just fine, but vdpau uses a lot less processor.

Anyone run into this problem?

---

### Post by pedja_portugalac on 2010-05-01
Did you installed vdpau nvidia driver and smplayer from ppa?

---

### Post by Shibblet on 2010-05-01
I didn't at first.  It worked fine with Karmic.  Then I did go download the vdpau PPA, and still I get nada.

---

### Post by andrew.46 on 2010-05-01
Hi Shibblet,

> **Shibblet said:**
> SMplayer has a vdpau option, turn it on, and it stops playing video. 

Can you give the logs for SMPlayer during the failure? Options --> View Logs.

Andrew

---

### Post by Jose Catre-Vandis on 2010-05-01
I had success as follows:

Put the vdpau ppa in sources
Installed x264 and ffmpeg
Installed vdpauinfo and libvdpau1
Installed mplayer-no-gui (my preference)

I tested smplayer and with the vdpau option that worked OK too.

This on Xubuntu 10.04

---

### Post by Shibblet on 2010-05-01
> **andrew.46 said:**
> Hi Shibblet,

Can you give the logs for SMPlayer during the failure? Options --> View Logs.

Andrew

Yep, looks like the crash was in Mplayer, not SMplayer.

```
/usr/bin/mplayer -noquiet -nofs -nomouseinput -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau, -sub-fuzziness 1 -identify -slave -vo vdpau -ao alsa -nokeepaspect -framedrop -dr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 41943377 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/kubais/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -subpos 100 -cache 2000 -ss 8 -osdlevel  -vf-add screenshot -vf-clr -slices -channels 2 -af equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 150 /media/Media/Movies/National Treasure 2 - Book of Secrets.m4v

bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing /media/Media/Movies/National Treasure 2 - Book of Secrets.m4v.

Cache fill:  0.00% (0 bytes)   
libavformat file format detected.
ID_VIDEO_ID=0
[lavf] Video stream found, -vid 0
ID_AUDIO_ID=1
[lavf] Audio stream found, -aid 1
ID_SUBTITLE_ID=0
[lavf] Subtitle stream found, -sid 0
VIDEO:  [avc1]  704x356  24bpp  90000.000 fps    0.0 kbps ( 0.0 kbyte/s)
ID_FILENAME=/media/Media/Movies/National Treasure 2 - Book of Secrets.m4v
ID_DEMUXER=lavfpref
ID_VIDEO_FORMAT=avc1
ID_VIDEO_BITRATE=0
ID_VIDEO_WIDTH=704
ID_VIDEO_HEIGHT=356
ID_VIDEO_FPS=90000.000
ID_VIDEO_ASPECT=2.3437
ID_AUDIO_FORMAT=255
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=6
ID_LENGTH=7473.55
ID_SEEKABLE=1
ID_CHAPTERS=0
[vdpau] Could not open dynamic library libvdpau.so.1
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [alsa] 48000Hz 2ch floatle (4 bytes per sample)
ID_AUDIO_CODEC=faad
Video: no video
Starting playback...
[Mixer] No hardware mixing, inserting volume filter.


MPlayer interrupted by signal 11 in module: key_events
ID_SIGNAL=11
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
 [ This binary of MPlayer in Debian is currently compiled with
   '--enable-debug'; the debugging symbols are in the package
   'mplayer-dbg'.]
```

---

### Post by Shibblet on 2010-05-01
After reading the logs, I went into synaptic and downloaded libvdpau.1

Problem Solved.

Thanks for the help!

---

### Post by Jose Catre-Vandis on 2010-05-02
Just out of interest, here is the output from vdpauinfo, what are we looking for in here, and what could be tweaked to make any improvements, if needed?

> jcv@lynx:~$ vdpauinfo
display: :0.0   screen: 0
API version: 1
Information string: NVIDIA VDPAU Driver Shared Library  195.36.15  Thu Mar 11 23:42:13 PST 2010

Video surface:

name   width height types
-------------------------------------------
420     4096  4096  NV12 YV12 
422     4096  4096  UYVY YUYV 

Decoder capabilities:

name               level macbs width height
-------------------------------------------
MPEG1                 0  8192  2048  2048
MPEG2_SIMPLE          3  8192  2048  2048
MPEG2_MAIN            3  8192  2048  2048
H264_MAIN            41  8190  2032  2048
H264_HIGH            41  8190  2032  2048
VC1_SIMPLE            1  8190  2048  2048
VC1_MAIN              2  8190  2048  2048
VC1_ADVANCED          4  8190  2048  2048

Output surface:

name              width height nat types
----------------------------------------------------
B8G8R8A8          8192  8192    y  Y8U8V8A8 V8U8Y8A8 
R10G10B10A2       8192  8192    y  Y8U8V8A8 V8U8Y8A8 

Bitmap surface:

name              width height
------------------------------
B8G8R8A8          8192  8192
R8G8B8A8          8192  8192
R10G10B10A2       8192  8192
B10G10R10A2       8192  8192
A8                8192  8192

Video mixer:

feature name                    sup
------------------------------------
DEINTERLACE_TEMPORAL             y
DEINTERLACE_TEMPORAL_SPATIAL     y
INVERSE_TELECINE                 y
NOISE_REDUCTION                  y
SHARPNESS                        y
LUMA_KEY                         y
HIGH QUALITY SCALING - L1        -
HIGH QUALITY SCALING - L2        -
HIGH QUALITY SCALING - L3        -
HIGH QUALITY SCALING - L4        -
HIGH QUALITY SCALING - L5        -
HIGH QUALITY SCALING - L6        -
HIGH QUALITY SCALING - L7        -
HIGH QUALITY SCALING - L8        -
HIGH QUALITY SCALING - L9        -

parameter name                  sup      min      max
-----------------------------------------------------
VIDEO_SURFACE_WIDTH              y         1     4096
VIDEO_SURFACE_HEIGHT             y         1     4096
CHROMA_TYPE                      y  
LAYERS                           y         0        4

attribute name                  sup      min      max
-----------------------------------------------------
BACKGROUND_COLOR                 y  
CSC_MATRIX                       y  
NOISE_REDUCTION_LEVEL            y      0.00     1.00
SHARPNESS_LEVEL                  y     -1.00     1.00
LUMA_KEY_MIN_LUMA                y  
LUMA_KEY_MAX_LUMA                y

---

### Post by Exaby1e on 2010-05-04
> **Shibblet said:**
> After reading the logs, I went into synaptic and downloaded libvdpau.1

Problem Solved.

Thanks for the help!

Thx for the tip, solved my problem too :D

---

### Post by pkchips on 2010-05-15
Instead of asking for libvdpau, I'm getting this:

[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.

What does it mean?

---

### Post by andrew.46 on 2010-05-15
This error:

```
bt_audio_service_open: connect() failed: Connection refused (111)
```

seems quite widespread in lucid and relates to bluetooth devices, not sure of the fix....

Andrew

---

### Post by pkchips on 2010-05-15
> **pkchips said:**
> Instead of asking for libvdpau, I'm getting this:

[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.

What does it mean?

Yep I have the bt audio error too, but video and audio works just fine as long as I don't use vdpau.

I have an Nvidia 7900GTX, does this card work with VDPAU?

When I run vdpauinfo, it gives me the same error i.e. error when calling vdp_device_create

---

### Post by Shibblet on 2010-05-16
I think you need the 8000 Series and up for vdpau.

---

### Post by abdusamed on 2010-06-26
I have the the 256 version nvidia card installed, also i have the option to choose vdpau option from the smplayer preferences option which means i have the real deal. When ever i try to play a hd video which i know gpu can decode or vdpau supports the decoding, i can't view any video only sound.... what the problem i really need to get this work!

---

### Post by smartmelvin on 2011-02-28
I am having problem with playing HD videos in 10.10 I changed the video output to vdpau in smplayer but dont get any video at all. with vx the output is paused. video works fine on xp in the same comp. I have nvidia graphics card. Can anybody help please!!!

---

