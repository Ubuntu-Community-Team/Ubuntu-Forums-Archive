---
title: "Failed To Get A/V Sync When Using VDPAU"
date: 2018-01-02
forum: Multimedia Software
---

### Post by PaulRSte on 2018-01-02
Have just reinstalled Ubuntu 16.04.1 and Mythtv 0.28 and am getting "Failed To Get A/V Sync When Using VDPAU" with both SD and HD test material and recorded programs. The graphics card is an ASUS ENGT520 which uses the Nvidia Geforce GT 520 chipset (according the the ASUS website). From what I have read on the MythTV VDPAU site and the Purevideo Wiki, this provides Purevideo feature set D and is capable of 4K resolution. The TV it is played through is 1080p so I would have thought that this was adequate and the card should therefore be capable of Full VDPAU support. I have had to set this to "Slim" to get it working.

I have seen on the forum that there are some issues with VDPAU so my questions are:-

1)    Should the card be capable of providing Full VDPAU support?

2)    If yes then is there anything I can do to get this working at this release of Ubuntu and MythTV?

3)   If a later release of Ubuntu and/ or MythTV is required then will my proposed replacement tuner card (Hauppauge WinTV QuadHD) work at that release as their PPA is only supported at 16.04.1 at present (something to do with the LTS Support Stacks at 16.04.2 and above).

Thanks in advance

---

### Post by Yellow Pasque on 2018-01-02
Look at (and post output of) vdpauinfo:
```
sudo apt-get install vdpauinfo
vdpauinfo
```

---

### Post by PaulRSte on 2018-01-03
> **Temüjin said:**
> Look at (and post output of) vdpauinfo:
```
sudo apt-get install vdpauinfo
vdpauinfo
```

Thanks - Output below as requested

paul@PVR-1:~$ vdpauinfo
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
MPEG2_SIMPLE                   --- not supported ---
MPEG2_MAIN                     --- not supported ---
H264_BASELINE                  --- not supported ---
H264_MAIN                      --- not supported ---
H264_HIGH                      --- not supported ---
VC1_SIMPLE                     --- not supported ---
VC1_MAIN                       --- not supported ---
VC1_ADVANCED                   --- not supported ---
MPEG4_PART2_SP                 --- not supported ---
MPEG4_PART2_ASP                --- not supported ---
DIVX4_QMOBILE                  --- not supported ---
DIVX4_MOBILE                   --- not supported ---
DIVX4_HOME_THEATER             --- not supported ---
DIVX4_HD_1080P                 --- not supported ---
DIVX5_QMOBILE                  --- not supported ---
DIVX5_MOBILE                   --- not supported ---
DIVX5_HOME_THEATER             --- not supported ---
DIVX5_HD_1080P                 --- not supported ---
H264_CONSTRAINED_BASELINE      --- not supported ---
H264_EXTENDED                  --- not supported ---
H264_PROGRESSIVE_HIGH          --- not supported ---
H264_CONSTRAINED_HIGH          --- not supported ---
H264_HIGH_444_PREDICTIVE       --- not supported ---
HEVC_MAIN                      --- not supported ---
HEVC_MAIN_10                   --- not supported ---
HEVC_MAIN_STILL                --- not supported ---
HEVC_MAIN_12                   --- not supported ---
HEVC_MAIN_444                  --- not supported ---

Output surface:

name              width height nat types
----------------------------------------------------
B8G8R8A8         16384 16384    y  NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8 A4I4 I4A4 A8I8 I8A8 
R8G8B8A8         16384 16384    y  NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8 A4I4 I4A4 A8I8 I8A8 
R10G10B10A2      16384 16384    y  NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8 A4I4 I4A4 A8I8 I8A8 
B10G10R10A2      16384 16384    y  NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8 A4I4 I4A4 A8I8 I8A8 

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
VIDEO_SURFACE_WIDTH              y        48     2048
VIDEO_SURFACE_HEIGHT             y        48     2048
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


paul@PVR-1:~$

---

### Post by Yellow Pasque on 2018-01-03
So do you intend to use the nvidia proprietary/binary driver? If not (i.e. you want to use open-source "nouveau" driver), you need to:
1. Install 'mesa-vdpau-drivers' package, which it looks like you already have.
2. Install the nouveau VDPAU firmware [https://nouveau.freedesktop.org/wiki/VideoAcceleration/](https://nouveau.freedesktop.org/wiki/VideoAcceleration/)

Extra credit: Edit the MythTV wiki to point out nouveau needs firmware that most distros won't provide because of legal reasons and link to the page.

---

### Post by PaulRSte on 2018-01-03
My first build of Ubuntu was in 2007 with Karmic(?) and I remember having to install an Nvidia driver, this for the built in graphics card on the  motherboard.  I was of the understanding that a few releases of Ubuntu later, the nVidia driver was included in the build. I bought the Asus card about five years ago when we got the widescreen TV.  The power supply blew 2 years ago and took everything out but the ASUS graphics card so it was completely rebuilt (at 14.04) without installing an Nvidia driver.  I had issues with the 16.04 upgrade and I was advised to do a re-install, which is why it has just been rebuilt again.  I have still not installed any Nvidia driver though, so I assume that the mesa-vdpau-drivers package is installed by default, or is part of the mythic package.

Am I right in thinking that there is a PPA for the proprietary driver, and that that would be the best option? If so, would I need to uninstall the mesa-vdpau-drivers package, before or after installing the proprietary driver?

---

### Post by Yellow Pasque on 2018-01-03
You don't need a PPA for the proprietary driver, though there is one available: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
I think most people use the "Additional Driver" utility though.

>  If so, would I need to uninstall the mesa-vdpau-drivers package, before or after installing the proprietary driver? 

It doesn't matter. You can even keep it. They coexist fine with proprietary driver(s).

---

### Post by PaulRSte on 2018-01-19
Hi Temüjin

Thanks for your help with this. Have used apt-get to install the driver package - version 384 - which is working fine on VDPAU High quality. On the back of this have just bought and installed an Hauppauge WinTV Quad HD tuner which just worked.  Have also sorted out the channel recording priorities to give preference to HD.  Took a bit of work as most of the posts assumed that the SD and HD tuners in a PC would be separate devices and to prioritise the tuners. Regardless of the physical build of the tuners on the card, each SD/HD pair is seen as one device, so this approach wouldn't work. Especially as some of the multiplexes transmit both HD and SD. I used the channel editor in the backend setup to give priority to the HD channels - works a treat.

Thanks again - Paul

---

