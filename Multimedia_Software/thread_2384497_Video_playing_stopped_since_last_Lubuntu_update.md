---
title: "Video playing stopped since last Lubuntu update"
date: 2018-02-08
forum: Multimedia Software
---

### Post by bacizone on 2018-02-08
Hi, 

since the last full update (07/02/2018), all video players in **Lubuntu **stopped working. Not sure but I think I started from Lubuntu 14.04 LTS and install updates regularly.

Neither VLC nor Gnome MPlayer plays any video: they just crash and exit when I load and press play on a simple mp4 video file that was playable previously (before the update) without any problem. 

Tried reinstalling the players, but it seems to be a Lubuntu problem. 

[B]When can I expect a hotfix for this serious defect?

[/B]thanks,
Baci

---

### Post by ajgreeny on 2018-02-08
This is not a general problem for most of us using Lubuntu 16.04, which is what I am using, fully updated, and not showing any video playing problems at all, even on this very old, slow netbook, (Atom 270, 1GB ram).

Try starting one of those videos that will not play in terminal with command ```
vlc Videos/filename.mp4
```changing that file-pathway for your own, of course, and report back here any error you see.

---

### Post by bacizone on 2018-02-08
I accomplished it, run cvlc in terminal on a simple mp4 file:

"VLC media player 2.2.2 Weatherwax (revision 2.2.2-0-g6259d80)
[08498e08] dummy interface: using the dummy interface module...
[afd07c58] vdpau_avcodec generic error: decoder profile not supported: 7
Segmentation fault (core dumped)"

It is Lubuntu 16.04.3 LTS (Linux 4.40-112-generic)
It is a Dell 1501 laptop with 2 GB RAM, and as I mentioned all was fine some days ago, before the last system update.

Currently there is no video file that it can play.

Please  help.

---

### Post by ajgreeny on 2018-02-08
That error suggests that you do not have the decoding codecs needed to play your videos.

Try installing the ubuntu-restricted-extras and libvdpau1 packages first and we can try to move forward from that.

---

### Post by bacizone on 2018-02-10
Ok, I installed both, installations went fine, but installing "libvdpau1" sent me this:
"libvdpau1 is already the newest version 1.1.1-3ubuntu1"

Unfortunately installing ubuntu-restricted-extras and trying to install libvdpau1 did not help at all, still getting the same symptom: 
video can be loaded, but pressing play crashes and exits any media player in Lubuntu now.

Please help.

---

### Post by Yellow Pasque on 2018-02-10
So what happens if you try to use a different video output (not VDPAU) in VLC?

Look at vdpauinfo and glxinfo for clue(s):
```
sudo apt-get install vdpauinfo
vdpauinfo
glxinfo | grep string
```

---

### Post by bacizone on 2018-02-12
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]Here are the details:

:~$ glxinfo|grep string[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]server glx vendor string: SGI[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]server glx version string: 1.4[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]client glx vendor string: Mesa Project and SGI[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]client glx version string: 1.4[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]OpenGL vendor string: [/FONT][/COLOR][X.Org]("http://x.org/")[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot] R300 Project[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]OpenGL renderer string: ATI RS480[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]OpenGL version string: 2.1 Mesa 17.2.4[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]OpenGL shading language version string: 1.20[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]OpenGL ES profile version string: OpenGL ES 2.0 Mesa 17.2.4[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]OpenGL ES profile shading language version string: OpenGL ES GLSL ES 1.0.16[/FONT][/COLOR]

[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]:~$ vdpauinfo[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]display: :0.0   screen: 0[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]API version: 1[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]Information string: G3DVL VDPAU Driver Shared Library version 1.0[/FONT][/COLOR]

[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]Video surface:[/FONT][/COLOR]

[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]name   width height types[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]-------------------------------------------[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]420     2048  2048  NV12 YV12 [/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]422     2048  2048  [/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]444     2048  2048  Y8U8V8A8 V8U8Y8A8 [/FONT][/COLOR]

[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]Decoder capabilities:[/FONT][/COLOR]

[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]name                        level macbs width height[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]----------------------------------------------------[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]MPEG1                           0 16384  2048  2048[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]MPEG2_SIMPLE                    3 16384  2048  2048[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]MPEG2_MAIN                      3 16384  2048  2048[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]H264_BASELINE                  --- not supported ---[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]H264_MAIN                      --- not supported ---[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]H264_HIGH                      --- not supported ---[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]VC1_SIMPLE                     --- not supported ---[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]VC1_MAIN                       --- not supported ---[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]VC1_ADVANCED                   --- not supported ---[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]MPEG4_PART2_SP                 --- not supported ---[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]MPEG4_PART2_ASP                --- not supported ---[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]DIVX4_QMOBILE                  --- not supported ---[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]DIVX4_MOBILE                   --- not supported ---[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]DIVX4_HOME_THEATER             --- not supported ---[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]DIVX4_HD_1080P                 --- not supported ---[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]DIVX5_QMOBILE                  --- not supported ---[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]DIVX5_MOBILE                   --- not supported ---[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]DIVX5_HOME_THEATER             --- not supported ---[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]DIVX5_HD_1080P                 --- not supported ---[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]H264_CONSTRAINED_BASELINE      --- not supported ---[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]H264_EXTENDED                  --- not supported ---[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]H264_PROGRESSIVE_HIGH          --- not supported ---[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]H264_CONSTRAINED_HIGH          --- not supported ---[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]H264_HIGH_444_PREDICTIVE       --- not supported ---[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]HEVC_MAIN                      --- not supported ---[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]HEVC_MAIN_10                   --- not supported ---[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]HEVC_MAIN_STILL                --- not supported ---[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]HEVC_MAIN_12                   --- not supported ---[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]HEVC_MAIN_444                  --- not supported ---[/FONT][/COLOR]

[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]Output surface:[/FONT][/COLOR]

[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]name              width height nat types[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]----------------------------------------------------[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]B8G8R8A8          2048  2048    y  NV12 YV12 Y8U8V8A8 V8U8Y8A8 A4I4 I4A4 A8I8 I8A8 [/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]R8G8B8A8          2048  2048    y  NV12 YV12 Y8U8V8A8 V8U8Y8A8 A4I4 I4A4 A8I8 I8A8 [/FONT][/COLOR]

[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]Bitmap surface:[/FONT][/COLOR]

[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]name              width height[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]------------------------------[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]B8G8R8A8          2048  2048[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]R8G8B8A8          2048  2048[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]A8                2048  2048[/FONT][/COLOR]

[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]Video mixer:[/FONT][/COLOR]

[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]feature name                    sup[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]------------------------------------[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]DEINTERLACE_TEMPORAL             y[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]DEINTERLACE_TEMPORAL_SPATIAL     -[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]INVERSE_TELECINE                 -[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]NOISE_REDUCTION                  y[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]SHARPNESS                        y[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]LUMA_KEY                         y[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]HIGH QUALITY SCALING - L1        y[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]HIGH QUALITY SCALING - L2        -[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]HIGH QUALITY SCALING - L3        -[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]HIGH QUALITY SCALING - L4        -[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]HIGH QUALITY SCALING - L5        -[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]HIGH QUALITY SCALING - L6        -[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]HIGH QUALITY SCALING - L7        -[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]HIGH QUALITY SCALING - L8        -[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]HIGH QUALITY SCALING - L9        -[/FONT][/COLOR]

[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]parameter name                  sup      min      max[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]-----------------------------------------------------[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]VIDEO_SURFACE_WIDTH              y        48     2048[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]VIDEO_SURFACE_HEIGHT             y        48     2048[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]CHROMA_TYPE                      y  [/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]LAYERS                           y         0        4[/FONT][/COLOR]

[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]attribute name                  sup      min      max[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]-----------------------------------------------------[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]BACKGROUND_COLOR                 y  [/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]CSC_MATRIX                       y  [/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]NOISE_REDUCTION_LEVEL            y      0.00     1.00[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]SHARPNESS_LEVEL                  y     -1.00     1.00[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]LUMA_KEY_MIN_LUMA                y  [/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&quot]LUMA_KEY_MAX_LUMA                y  


Anyway, as I do not have time to track this issue, I clean-installed a fresh 17.10 and video playback works again without any problem.

This is not the first time a Linux update kills a vital function...  for free I can accept it, but not really good.[/FONT][/COLOR]

---

