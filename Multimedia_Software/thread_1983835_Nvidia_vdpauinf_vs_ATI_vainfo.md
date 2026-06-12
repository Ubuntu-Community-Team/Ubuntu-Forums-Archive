---
title: "Nvidia vdpauinf vs ATI vainfo"
date: 2012-05-20
forum: Multimedia Software
---

### Post by Azyx on 2012-05-20
I have a Nvidia GT 520 and AMD/ATI are E450 1,6GB Dual core processor with HD6320 igfx (Fusion

```
**Azyx@Intel:~$ vdpauinfo**
display: :0.0   screen: 0
API version: 1
Information string: NVIDIA VDPAU Driver Shared Library  295.53  Fri May 11 23:39:26 PDT 2012

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
**[COLOR="red"]H264_HIGH            41  8192  2048  2048[/COLOR]**
VC1_SIMPLE            1  8190  2048  2048
VC1_MAIN              2  8190  2048  2048
**[COLOR="red"]VC1_ADVANCED          4  8190  2048  2048[/COLOR]**
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


**Azyx@Blackus:~$ vainfo**
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      [B][COLOR="Red"]VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD[/COLOR][/B]
```

Does the AMD/ATI have only 2 types of hardware video-acceleration and NVidia 18 different types of videoformat to accelerate, or is it only diffent way to show the acceleration?

And all type of tips and also links to furher reading are apriciatet. /Cheers

---

### Post by Nutria on 2012-05-22
vaapi is known to be less featureful than vdpau, so maybe that's the case.

Also, please wrap your CLI output in CODE blocks.

---

### Post by Azyx on 2012-05-22
> **Nutria said:**
>  Also, please wrap your CLI output in CODE blocks.

how? Is not CLI a technic thre you have 2 gfx at same computer?

---

### Post by Nutria on 2012-05-22
> how? Is not CLI a technic thre you have 2 gfx at same computer?

:)  That's SLI.

---

### Post by Azyx on 2012-05-22
> **Nutria said:**
> :)  That's SLI.

yes. Morning. cli commander line interface..

---

### Post by Azyx on 2012-05-23
> **KayleJamason said:**
> I always work with  Nvidia vdpauinf  and it functions good I think

I have a problem with H264 (low resolution, not HD-videos) The video being better and with less flickering without hardware acceleration, played with XBMP with XvBA support.

---

### Post by Azyx on 2012-07-19
Bump

How is it really? Does Nvidia AV-acceleration support more types of compressed videos, and make them more view-able? Nvidia maybe add more noise to make the high compessed video looks better?

/Cheers

---

