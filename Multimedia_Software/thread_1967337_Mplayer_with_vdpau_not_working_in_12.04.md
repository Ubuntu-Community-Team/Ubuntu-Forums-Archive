---
title: "Mplayer with vdpau not working in 12.04"
date: 2012-04-28
forum: Multimedia Software
---

### Post by ergo-proxy on 2012-04-28
Hi, just made a clean installation of 12.04x64 and I'm having problems with playing videos using vdpau and gnome mplayer (mplayer too).

 In gnome mplayer settings I have set vdpau (like did always before) and I don't get any picture, just sound and if I change output to for example to GL it works fine but consumes cpu :/

Tried with both nvidia-current and nvidia-current-update drivers but still the same, my GPU is GTX460. 

I download vdpauinfo, here is the output... but I don't see anything wrong in it. What else could be wrong? Never had this problem before.

```
display: :0.0   screen: 0
API version: 1
Information string: NVIDIA VDPAU Driver Shared Library  295.40  Thu Apr  5 22:02:06 PDT 2012

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
H264_MAIN            41  8192  2048  2048
H264_HIGH            41  8192  2048  2048
VC1_SIMPLE            1  8190  2048  2048
VC1_MAIN              2  8190  2048  2048
VC1_ADVANCED          4  8190  2048  2048
MPEG4_PART2_SP        3  8192  2048  2048
MPEG4_PART2_ASP       5  8192  2048  2048
DIVX4_QMOBILE         0  8192  2048  2048
DIVX4_MOBILE          0  8192  2048  2048
DIVX4_HOME_THEATER    0  8192  2048  2048
DIVX4_HD_1080P        0  8192  2048  2048
DIVX5_QMOBILE         0  8192  2048  2048
DIVX5_MOBILE          0  8192  2048  2048
DIVX5_HOME_THEATER    0  8192  2048  2048
DIVX5_HD_1080P        0  8192  2048  2048

Output surface:

name              width height nat types
----------------------------------------------------
B8G8R8A8         16384 16384    y  Y8U8V8A8 V8U8Y8A8 
R10G10B10A2      16384 16384    y  Y8U8V8A8 V8U8Y8A8 

Bitmap surface:

name              width height
------------------------------
B8G8R8A8         16384 16384
R8G8B8A8         16384 16384
R10G10B10A2      16384 16384
B10G10R10A2      16384 16384
A8               16384 16384

Video mixer:

feature name                    sup
------------------------------------
DEINTERLACE_TEMPORAL             y
DEINTERLACE_TEMPORAL_SPATIAL     y
INVERSE_TELECINE                 y
NOISE_REDUCTION                  y
SHARPNESS                        y
LUMA_KEY                         y
HIGH QUALITY SCALING - L1        y
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

```

---

### Post by ergo-proxy on 2012-04-28
mplayer -vc ffh264vdpau -fs file.mkv plays the picture but it's choppy :(

---

### Post by SeijiSensei on 2012-04-28
You can try installing a newer version of mplayer as I described [here](http://ubuntuforums.org/showpost.php?p=11882074&postcount=2).  

These days I'm using mplayer2 from [http://www.mplayer2.org/](http://www.mplayer2.org/) built from source.  You can also install one from a PPA as described [here](http://www.ubuntugeek.com/install-mplayer2-on-ubuntu-using-ppa.html).  The one I built from source works fine with my 9500GT and vdpau even on 1080p 10bit H.264 encodes.

By the way, Vincent, I just happened to watch you on that game show tonight!  That Real is sure one hot number, but I have to say I love Pino more.

---

### Post by ergo-proxy on 2012-04-28
Thx, I updated mplayer but it did not resolve the problem. I noticed that mplayer consumes over 100% CPU with vdpau :/

```
MPlayer2 UNKNOWN (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing testvideo.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3), -aid 0, -alang eng
[mkv] Track ID 3: subtitles (S_TEXT/UTF8), -sid 0, -slang eng
[mkv] Will play video track 1.
Detected file format: Matroska
VIDEO:  [avc1]  1280x544  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Load subtitles in .
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Asking decoder to use 4 threads if supported.
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 640.0 kbit/41.67% (ratio: 80000->192000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 2.35:1 - prescaling to correct movie aspect.
VO: [vdpau] 1280x544 => 1280x544 Planar YV12 
[vdpau] Got display refresh rate 59.883 Hz.
[vdpau] If that value looks wrong give the -vo vdpau:fps=X suboption manually.
A:  24.3 V:  24.4 A-V: -0.000 ct:  0.000   0/  0  1% 43%  0.6% 0 0 

```

---

### Post by SeijiSensei on 2012-04-28
Which mplayer are you using?

```
MPlayer2 UNKNOWN (C) 2000-2012 MPlayer Team
```

I just installed the version in the [daily build PPA]("https://launchpad.net/~motumedia/+archive/mplayer-daily") and see:

```
MPlayer SVN-r34707-4.6 (C) 2000-2012 MPlayer Team
```

If I use "-vc ffh264vdpau" with that version of mplayer, it reports using acceleration, and my CPUs are all around 3%.  Without acceleration, one of my cores is pushing 100%.

The one problem I have with the official version of mplayer is that it crashes with 10-bit encodes if I use VDPAU, though not with xv.  However the version of mplayer2 (dated 3/27) that I built from [source]("http://ftp.mplayer2.org/pub/archive/release/linux/") this evening played a 1080p 10-bit encode with VDPAU just fine.  If you're not averse to trying to compile your own player, I'd give that a shot. Make sure you run

```
sudo apt-get build-dep mplayer
```

to install any needed libraries and headers before compiling.

---

### Post by ergo-proxy on 2012-04-28
Woot! It seems mplayer wasn't updated properly. Now when I purged it and installed it from ppa it did finally show the right version... and played like a charm without even touch CPU! It seems gnome mplayer coming from the default repository is bugged.

Thank you very much Senji! :)

---

### Post by giantjoebot on 2012-12-01
How did you purge and update it exactly?

---

