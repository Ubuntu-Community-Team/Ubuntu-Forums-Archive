---
title: "Mythbuntu AMD Kabini frontend shutdown issues"
date: 2014-12-17
forum: Mythbuntu
---

### Post by Lester_Burnham on 2014-12-17
Hi,

I recently purchased an AMD Kabini based ASRock QC5000-ITX to use as a 0.27 frontend for TV and XBMC for movies.
It has been set it up to use mesa for VDPAU hardware acceleration, by installing mesa-vdpau-drivers.
The machine works fine in mythtv using VDPAU slim and XBMC watching 1080p with low CPU.
I have temporarily added a launcher to the tool bar to shut the machine down. mythtv & XBMC both shut the machine down OK from their menus.

The problem:
When I use the desktop menu to log out or shut down the machine, the dialogue does not appear and the applications menu becomes sluggish. If I go to Alt+F7, I can see the dialogue box and can cancel it or use it to shut down etc.

The machine is up to date running:
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"

mythfrontend --version:
Please attach all output as a file in bug reports.
MythTV Version : v0.27-193-g8ee257c
MythTV Branch : fixes/0.27
Network Protocol : 77
Library API : 0.27.20140323-1
QT Version : 4.8.6

glxgears gives me:
GL_RENDERER   = Gallium 0.4 on AMD KABINI
GL_VERSION    = 3.0 Mesa 10.1.3
GL_VENDOR     = X.Org

vdpauinfo gives:
display: :0.0   screen: 0
API version: 1
Information string: G3DVL VDPAU Driver Shared Library version 1.0

Video surface:

name   width height types
-------------------------------------------
420    16384 16384  NV12 YV12 
422    16384 16384  
444    16384 16384  Y8U8V8A8 V8U8Y8A8 

Decoder capabilities:

name               level macbs width height
-------------------------------------------
MPEG1                 0  9216  2048  1152
MPEG2_SIMPLE          3  9216  2048  1152
MPEG2_MAIN            3  9216  2048  1152
H264_BASELINE        41  9216  2048  1152
H264_MAIN            41  9216  2048  1152
H264_HIGH            41  9216  2048  1152
VC1_ADVANCED          4  9216  2048  1152
MPEG4_PART2_SP        3  9216  2048  1152
MPEG4_PART2_ASP       5  9216  2048  1152

Output surface:

name              width height nat types
----------------------------------------------------
B8G8R8A8         16384 16384    y  NV12 YV12 Y8U8V8A8 V8U8Y8A8 
R8G8B8A8         16384 16384    y  NV12 YV12 Y8U8V8A8 V8U8Y8A8 
R10G10B10A2      16384 16384    y  NV12 YV12 Y8U8V8A8 V8U8Y8A8 
B10G10R10A2      16384 16384    y  NV12 YV12 Y8U8V8A8 V8U8Y8A8 

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
LUMA_KEY                         -
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
VIDEO_SURFACE_WIDTH              y        48     2048
VIDEO_SURFACE_HEIGHT             y        48     1152
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

Sorry in advance for the information overload or lack of useful info.
Other things I have tried, is to reset the desktop to defaults by deleting the cache. This did not help.

Any ideas where to look?
Thanks,
Lester

---

### Post by jds2 on 2014-12-22
I think I have the same problem. When you take a screenshot, is there also a long delay? Do you notice Xorg using a lot of CPU when things get unresponsive? You may want to have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=2232737") where other people are describing similar issues on similar hardware.

---

### Post by Lester_Burnham on 2014-12-23
Hi,

Thanks for the reply.  I hadn't seen that thread.
I remember seeing xorg hovering around 25%, but hadn't tried any screen captures. (Nothing was 100% cpu anyway)
I might also post over at the xbmc forums, where they're actively messing with VDPAU and Kabini.

Lester

---

