---
title: "Failed to initialize video output"
date: 2013-01-22
forum: Mythbuntu
---

### Post by avoa on 2013-01-22
Hi,

Can somebody help me. I got very boring problem with Mythtv. 
After reboot Mythtv can play back Recordings from TV. But after certain time it gives error Failed to initialize video output. It seems Mythtv tries to open video playback, it shows Please wait... and then after 20 seconds error appears. Reboot helps and playback works. 
Half year ago I didn't had this problem. Then I got it once a week, now it appears almost every day after watching few recordings. So, this is not permanent problem, but appears sometimes. Yesterday after reboot I watched 2 recordings, but today I got an error. 
I tried to search from Internet, but didn't find solution.
My recordings are in H.264 format. When this problem appears, then I cannot watch TV and videos also. VLC works fine.
What might be wrong?

Additional information:

**Ubuntu**:
Release 12.10 (quantal) 64-bit
Kernel Linux 3.5.0-22-generic
GNOME 3.6.0
Processor: AMD 64
Memory: 2.9 GiB
Graphics Processor: GeForce 8500 GT Using FullHD 1920x1080 pixels monitor
Memory: 512 MB
NVIDIA Driver Version: 304.43

Mythtv log:
2013-01-22 13:58:08.581780 I  TV: Attempting to change from None to WatchingPreRecorded
2013-01-22 13:58:08.656558 E  ALSA: snd_pcm_info_get_card: Operation not permitted
2013-01-22 13:58:08.671468 N  AudioPlayer: Enabling Audio
2013-01-22 13:58:08.710453 I  AFD: Opened codec 0x5d55910, id(H264) type(Video)
2013-01-22 13:58:08.710480 I  AFD: codec MP2 has 2 channels
2013-01-22 13:58:08.710536 I  AFD: Opened codec 0x606d450, id(MP2) type(Audio)
2013-01-22 13:58:08.710646 I  AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2013-01-22 13:58:08.742943 E  ALSA: no playback control PCM found on mixer device default
2013-01-22 13:58:08.742967 E  ALSA: Unable to open audio mixer. Volume control disabled
2013-01-22 13:58:08.891318 E  **VDPAU: Error at mythrender_vdpau.cpp:603 (#23, The system does not have enough resources to complete the requested operation at this time.)**
2013-01-22 13:58:08.891334 E  VDPAU: Failed to create output surface.
2013-01-22 13:58:08.891341 E  VDPAU: No presentation surfaces
2013-01-22 13:58:08.891346 E  VDPAU: Failed to create VDPAU render device.
2013-01-22 13:58:08.891354 E  VidOutVDPAU: Failed to initialise VDPAU
2013-01-22 13:58:08.928154 E  VideoOutput: Not compiled with any useable video output method.
2013-01-22 13:58:08.928179 E  Player(0): Couldn't create VideoOutput instance. Exiting..
2013-01-22 13:58:08.928199 E  Player(0): Unable to initialize video.
2013-01-22 13:58:28.960649 E  playCtx: StartPlaying() Failed to start player
2013-01-22 13:58:28.974396 I  TV: Main UI disabled.

avo@MediaU:~$ xset q
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    off    02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  500    repeat rate:  33
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  no    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0x0    WhitePixel:  0xffffff
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On

avo@MediaU:~$ glxinfo | grep OpenGL
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8500 GT/PCIe/SSE2
OpenGL version string: 3.3.0 NVIDIA 304.43
OpenGL shading language version string: 3.30 NVIDIA via Cg compiler
OpenGL extensions:
avo@MediaU:~$ grep -i vdpau /var/log/Xorg.0.log
[    29.453] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
avo@MediaU:~$ vdpauinfo
display: :0   screen: 0
API version: 1
Information string: NVIDIA VDPAU Driver Shared Library  304.43  Sun Aug 19 20:36:15 PDT 2012

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

Avo

---

### Post by avoa on 2013-01-22
Hi again,
I noticed that, after I got this error, I changed from Mythtv Settings-> Video -> Playback -> Current video playback profile: from VDPAU High Quality to High quality (ffmplay & XVideo) and playback starts to work without reboot. 
So the problem is in VDPAU.
Is this a "feature" of NVIDIA driver? Or should be VDPAU setup changed? Then what should be changed?

Avo

---

