---
title: "Hardware acceleration enabled but not working?"
date: 2018-05-10
forum: Multimedia Software
---

### Post by jeo7 on 2018-05-10
Hardware acceleration is enabled because if I run
```
glxinfo | grep "direct rendering"
 
```

Then I get

```
direct rendering: Yes

```

But if I run the following from a terminal:<br>

```

mpv --hwdec=vdpau B.mp4 
```

then the video plays for a few seconds after which the video stops and the terminal keeps writing this:
```
 
AV: 00:00:13 / 00:03:52 (5%) A-V: &nbsp;0.000
[vo/opengl] Mapping hardware decoded surface failed.
AV: 00:00:13 / 00:03:52 (5%) A-V: &nbsp;0.000
[vo/opengl] Mapping hardware decoded surface failed.

```

Printing this out continues until the end of the file is reached (I guess).<br><br>So it appears to me that HW acceleration is enabled but not working properly. Does anyone have any ideas on how to remedy this? Thanks in advance.

---

### Post by kerry_s on 2018-05-10
you have the ubuntu-restricted-extras installed? you try a different mp4?

---

### Post by Yellow Pasque on 2018-05-10
CHeck output of vdpauinfo in addition to above suggestion:
```
sudo apt-get install vdpauinfo
vdpauinfo
```

---

### Post by jeo7 on 2018-05-10
> **kerry_s said:**
> you have the ubuntu-restricted-extras installed? you try a different mp4?

Yes, that was one of the first things I installed. And yes, I have tried a different mp4 with the same result.

---

### Post by jeo7 on 2018-05-10
> **Temüjin said:**
> CHeck output of vdpauinfo in addition to above suggestion:
```
sudo apt-get install vdpauinfo
vdpauinfo
```

Here is the output vdpauinfo:

```
display: :0   screen: 0
API version: 1
Information string: G3DVL VDPAU Driver Shared Library version 1.0

Video surface:

name   width height types
-------------------------------------------
420    16384 16384  NV12 YV12 
422    16384 16384  UYVY YUYV 
444    16384 16384  Y8U8V8A8 V8U8Y8A8 

Decoder capabilities:

name                        level macbs width height
----------------------------------------------------
MPEG1                          --- not supported ---
MPEG2_SIMPLE                    3 65536  4096  4096
MPEG2_MAIN                      3 65536  4096  4096
H264_BASELINE                  52 65536  4096  4096
H264_MAIN                      52 65536  4096  4096
H264_HIGH                      52 65536  4096  4096
VC1_SIMPLE                      1 65536  4096  4096
VC1_MAIN                        2 65536  4096  4096
VC1_ADVANCED                    4 65536  4096  4096
MPEG4_PART2_SP                  3 65536  4096  4096
MPEG4_PART2_ASP                 5 65536  4096  4096
DIVX4_QMOBILE                  --- not supported ---
DIVX4_MOBILE                   --- not supported ---
DIVX4_HOME_THEATER             --- not supported ---
DIVX4_HD_1080P                 --- not supported ---
DIVX5_QMOBILE                  --- not supported ---
DIVX5_MOBILE                   --- not supported ---
DIVX5_HOME_THEATER             --- not supported ---
DIVX5_HD_1080P                 --- not supported ---
H264_CONSTRAINED_BASELINE       0 65536  4096  4096
H264_EXTENDED                  --- not supported ---
H264_PROGRESSIVE_HIGH          --- not supported ---
H264_CONSTRAINED_HIGH          --- not supported ---
H264_HIGH_444_PREDICTIVE       --- not supported ---
HEVC_MAIN                      186 65536  4096  4096
HEVC_MAIN_10                   --- not supported ---
HEVC_MAIN_STILL                --- not supported ---
HEVC_MAIN_12                   --- not supported ---
HEVC_MAIN_444                  --- not supported ---

Output surface:

name              width height nat types
----------------------------------------------------
B8G8R8A8         16384 16384    y  NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8 A8I8 I8A8 
R8G8B8A8         16384 16384    y  NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8 A8I8 I8A8 
R10G10B10A2      16384 16384    y  NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8 A8I8 I8A8 
B10G10R10A2      16384 16384    y  NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8 A8I8 I8A8 

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
DEINTERLACE_TEMPORAL_SPATIAL     -
INVERSE_TELECINE                 -
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
VIDEO_SURFACE_WIDTH              y        48     4096
VIDEO_SURFACE_HEIGHT             y        48     4096
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

### Post by mc4man on 2018-05-10
Try```
 mpv --no-config --log-file=mpv-log.txt --hwdec=yes B.mp4
```
The log will be in home folder, attach to a post

---

### Post by jeo7 on 2018-05-10
Here is the log file. I exited mpv after a while or else I'm not sure how long it would go on for. But it's repeating the same thing. I had to zip the file because it "exceeded the forum limit for files of this type."

---

### Post by mc4man on 2018-05-10
Can't help you out with ati as never had one. Out of curiousity what happens if you just go 
mpv B.mp4

---

### Post by jeo7 on 2018-05-10
> **mc4man said:**
> Can't help you out with ati as never had one. 

What do you mean by ati?

> Out of curiousity what happens if you just go 
mpv B.mp4 

The video plays. Here is what is reported in the terminal:

```
Playing: B.mp4
 (+) Video --vid=1 (*) (h264 854x480 29.970fps)
 (+) Audio --aid=1 --alang=und (*) (aac 2ch 44100Hz)
VO does not support requested hardware decoder, or loading it failed.
AO: [pulse] 44100Hz stereo 2ch float
VO: [opengl] 854x480 yuv420p
(Paused) AV: 00:00:28 / 00:03:52 (12%) A-V:  0.000


Exiting... (Quit)

```

---

### Post by mc4man on 2018-05-11
I mean an ati/amd video card.
It would seem the driver in use isn't supported for vdpau in mpv. You could try using --vo=vdpau --hwdec=vdpau though probably wouldn't help..
(- are you using an xorg or wayland session? If later then try in an  xorg (the default) session

---

### Post by jeo7 on 2018-05-11
> **mc4man said:**
> 
You could try using --vo=vdpau --hwdec=vdpau though probably wouldn't help.


Actually, [B]it made a huge difference:
[/B]
```
 $ mpv --vo=vdpau --hwdec=vdpau B.mp4Playing: B.mp4
 (+) Video --vid=1 (*) (h264 854x480 29.970fps)
 (+) Audio --aid=1 --alang=und (*) (aac 2ch 44100Hz)
AO: [pulse] 44100Hz stereo 2ch float
Using hardware decoding (vdpau).
VO: [vdpau] 854x480 vdpau[yuv420p]
[vo/vdpau] Compositing window manager detected. Assuming timing info is inaccurate.
AV: 00:00:46 / 00:03:52 (20%) A-V:  0.000




Exiting... (Quit)



```

What is the difference between the two commands?

As far as which session I'm using, right now I'm using Xorg and have been for a while. By the way, one of the problems is that it is not really a video card but integrated graphics. As was explained to me by AMD, none of the Linux AMD drivers will work because it is not one of the discrete graphics cards.

Thanks for your help.

---

### Post by mc4man on 2018-05-11
The default vo for mpv 0.27  is opengl, occasionally using a vo of vdpau or vaapi is beneficial  to certain hardware. So  it appears in your case the amd card & drivers you have can use vdpau hwdec but only with a vo of vdpau.

---

### Post by jeo7 on 2018-05-11
> **mc4man said:**
> The default vo for mpv 0.27  is opengl, occasionally using a vo of vdpau or vaapi is beneficial  to certain hardware. So  it appears in your case the amd card & drivers you have can use vdpau hwdec but only with a vo of vdpau.

Is there a way to permanently set vo=vdpau, i.e. is there a config file somewhere?

---

### Post by mc4man on 2018-05-11
> **jeo7 said:**
> Is there a way to permanently set vo=vdpau, i.e. is there a config file somewhere?
Sure, in ~/.config/mpv create a file named mpv.conf

In this file most cli options can be set, just don't use --
So 
vo=vdpau
hwdec=vdpau

If playing a file not supported in hwdec then using the vo of vdpau may not be best choice. If in such an instance there are poor results try from cli with --no-config option

---

### Post by mc4man on 2018-05-11
At some point you could try my ppa for mpv, updated often. read here completely before using
[https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests)

If so I'd suggest adding mpv to either unity or gnome-shell dock, the r. click on launcher icon will present you with useful info, links, ect.

---

### Post by jeo7 on 2018-05-11
Thank you so much!

---

### Post by jeo7 on 2018-05-12
I'm going to mark this solved.

---

