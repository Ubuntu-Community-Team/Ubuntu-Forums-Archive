---
title: "webcam not working, resolution problems ?"
date: 2013-08-28
forum: Multimedia Software
---

### Post by zyd33ns on 2013-08-28
I am trying to view my webcam using guvcviewer. At high resolution (640x480), I get a totally black screen. At lower resolution (320x240) I get pixels in the upper half of the screen that are very jittery. They seem to recognize color because when I put a sheet of paper near the apperture, the pixels become white. 

Here is the output of guvcviewer --verbose:

```
guvcview 1.1.3
video_device: /dev/video0
vid_sleep: 0
cap_meth: 1
resolution: 320 x 240
windowsize: 480 x 700
vert pane: 578
spin behavior: 0
mode: yuyv
fps: 1/30
Display Fps: 1
bpp: 0
hwaccel: 1
avi_format: 0
sound: 1
sound Device: 6
sound samp rate: 0
sound Channels: 0
Sound Block Size: 1 seconds
Sound Format: 80 
Sound bit Rate: 160 Kbps
Pan Step: 2 degrees
Tilt Step: 2 degrees
Video Filter Flags: 0
image inc: 0
profile(default):/drive/home/gabriel/default.gpfl
starting portaudio...
language catalog=> dir:/usr/share/locale type:UTF-8 lang:en_US.utf8 cat:guvcview.mo
yuyv: setting format to 1448695129
capture method = 1
video device: /dev/video0 
/dev/video0 - device 1
Init. Vimicro USB Camera (Altair) (location: usb-0000:00:1d.7-7)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/15, 
checking format: 1448695129
vid:0ac8 
pid:3450 
driver:uvcvideo
Controls:
control[0]: 0x980900  Brightness, -10:1:10, default 0
control[1]: 0x980901  Contrast, 0:1:20, default 10
control[2]: 0x980902  Saturation, 0:1:10, default 7
control[3]: 0x98090c  White Balance Temperature, Auto, 0:1:1, default 1
control[4]: 0x980918  Power Line Frequency, 0:1:2, default 1
control[5]: 0x98091a  White Balance Temperature, 2800:1:6500, default 6500
control[6]: 0x98091b  Sharpness, 0:1:10, default 2
control[7]: 0x98091c  Backlight Compensation, 0:1:2, default 0
control[8]: 0x9a0901  Exposure, Auto, 0:1:3, default 3
control[9]: 0x9a0902  Exposure (Absolute), 8:1:16384, default 512
resolutions of 1º format=5 
frame rates of 3º resolution=2 
Def. Res: 2  numb. fps:2
--------------------------------------- device #0
Name                     = Intel ICH5: Intel ICH5 (hw:0,0)
Host API                 = ALSA
Max inputs = 2, Max outputs = 6
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #1
Name                     = Intel ICH5: Intel ICH5 - MIC ADC (hw:0,1)
Host API                 = ALSA
Max inputs = 2, Max outputs = 0
Def. low input latency   =    0.011
Def. low output latency  =   -1.000
Def. high input latency  =    0.043
Def. high output latency =   -1.000
Def. sample rate         = 48000.00
--------------------------------------- device #2
Name                     = Intel ICH5: Intel ICH5 - MIC2 ADC (hw:0,2)
Host API                 = ALSA
Max inputs = 2, Max outputs = 0
Def. low input latency   =    0.011
Def. low output latency  =   -1.000
Def. high input latency  =    0.043
Def. high output latency =   -1.000
Def. sample rate         = 48000.00
--------------------------------------- device #3
Name                     = Intel ICH5: Intel ICH5 - ADC2 (hw:0,3)
Host API                 = ALSA
Max inputs = 2, Max outputs = 0
Def. low input latency   =    0.011
Def. low output latency  =   -1.000
Def. high input latency  =    0.043
Def. high output latency =   -1.000
Def. sample rate         = 48000.00
--------------------------------------- device #4
Name                     = Intel ICH5: Intel ICH5 - IEC958 (hw:0,4)
Host API                 = ALSA
Max inputs = 0, Max outputs = 2
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #5
Name                     = front
Host API                 = ALSA
Max inputs = 0, Max outputs = 6
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #6
Name                     = surround40
Host API                 = ALSA
Max inputs = 0, Max outputs = 4
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #7
Name                     = surround41
Host API                 = ALSA
Max inputs = 0, Max outputs = 128
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #8
Name                     = surround50
Host API                 = ALSA
Max inputs = 0, Max outputs = 128
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #9
Name                     = surround51
Host API                 = ALSA
Max inputs = 0, Max outputs = 6
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #10
Name                     = iec958
Host API                 = ALSA
Max inputs = 0, Max outputs = 2
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #11
Name                     = spdif
Host API                 = ALSA
Max inputs = 0, Max outputs = 2
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #12
Name                     = pulse
Host API                 = ALSA
Max inputs = 32, Max outputs = 32
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #13
Name                     = dmix
Host API                 = ALSA
Max inputs = 0, Max outputs = 2
Def. low input latency   =   -1.000
Def. low output latency  =    0.043
Def. high input latency  =   -1.000
Def. high output latency =    0.043
Def. sample rate         = 48000.00
--------------------------------------- device #14
[ Default Input, Default Output ]
Name                     = default
Host API                 = ALSA
Max inputs = 32, Max outputs = 32
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #15
[ Default OSS Input, Default OSS Output ]
Name                     = /dev/dsp
Host API                 = OSS
Max inputs = 16, Max outputs = 16
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
----------------------------------------------
SampleRate:0 Channels:0
Video driver: x11
A window manager is available
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 
```

---

### Post by zyd33ns on 2013-08-28
I connected it to a different USB port and it works.... I hate computers.

---

