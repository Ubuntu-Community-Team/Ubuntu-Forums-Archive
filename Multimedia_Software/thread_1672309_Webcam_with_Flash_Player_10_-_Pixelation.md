---
title: "Webcam with Flash Player 10 - Pixelation"
date: 2011-01-20
forum: Multimedia Software
---

### Post by Kat of Zion on 2011-01-20
Im having issues with webcam when it is being "seen" via browsers.  Im running Flash Player 10 in  64 bit.  On things like Skype and previewing through Cheese, the pic looks fine. However, in Flash Player (using Firefox, Chrome or even Flock), the image that it grabs has square pixelation to it.  

Any reason why this is?

---

### Post by Kat of Zion on 2011-01-20
Well, "pixelation" might not be the right word.  It is possible that Flash Player is interlacing the pic despite that guvcview, cheese, camstream, and Skype do not.

Output of verbose from guvcview: 

```

guvcview 1.1.3
video_device: /dev/video0
vid_sleep: 0
cap_meth: 1
resolution: 640 x 480
windowsize: 792 x 716
vert pane: 578
spin behavior: 0
mode: yuyv
fps: 1/30
Display Fps: 1
bpp: 0
hwaccel: 1
avi_format: 1
sound: 1
sound Device: 3
sound samp rate: 9
sound Channels: 2
Sound Block Size: 1 seconds
Sound Format: 1 
Sound bit Rate: 160 Kbps
Pan Step: 2 degrees
Tilt Step: 2 degrees
Video Filter Flags: 0
image inc: 0
profile(default):/home/lixen69y2k/externalwebcamsettings01.gpfl
starting portaudio...
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
language catalog=> dir:/usr/share/locale type:UTF-8 lang:en_US.UTF-8 cat:guvcview.mo
yuyv: setting format to 1448695129
capture method = 1
video device: /dev/video0 
/dev/video0 - device 1
/dev/video1 - device 2
Init. UVC Camera (046d:0994) (location: usb-0000:00:1d.7-4)
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 800, height = 600 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
	Time interval between frame: 1/15, 1/10, 1/5, 
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 800, height = 600 }
	Time interval between frame: 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
	Time interval between frame: 1/10, 1/5, 
{ discrete: width = 1600, height = 1200 }
	Time interval between frame: 1/5, 
checking format: 1448695129
vid:046d 
pid:0994 
driver:uvcvideo
Adding control for Pan (relative)
UVCIOC_CTRL_ADD - Error: Operation not permitted
Adding control for Tilt (relative)
UVCIOC_CTRL_ADD - Error: Operation not permitted
Adding control for Pan Reset
UVCIOC_CTRL_ADD - Error: Operation not permitted
Adding control for Tilt Reset
UVCIOC_CTRL_ADD - Error: Operation not permitted
Adding control for Pan/tilt Reset
UVCIOC_CTRL_ADD - Error: Operation not permitted
Adding control for Focus (absolute)
UVCIOC_CTRL_ADD - Error: Operation not permitted
mapping control for Pan (relative)
UVCIOC_CTRL_MAP - Error: Operation not permitted
mapping control for Tilt (relative)
UVCIOC_CTRL_MAP - Error: Operation not permitted
mapping control for Pan Reset
UVCIOC_CTRL_MAP - Error: Operation not permitted
mapping control for Tilt Reset
UVCIOC_CTRL_MAP - Error: Operation not permitted
mapping control for Pan/tilt Reset
UVCIOC_CTRL_MAP - Error: Operation not permitted
mapping control for Focus (absolute)
UVCIOC_CTRL_MAP - Error: Operation not permitted
mapping control for LED1 Mode
UVCIOC_CTRL_MAP - Error: Operation not permitted
mapping control for LED1 Frequency
UVCIOC_CTRL_MAP - Error: Operation not permitted
mapping control for Disable video processing
UVCIOC_CTRL_MAP - Error: Operation not permitted
mapping control for Raw bits per pixel
UVCIOC_CTRL_MAP - Error: Operation not permitted
Controls:
control[0]: 0x980900  Brightness, 0:1:255, default 128
control[1]: 0x980901  Contrast, 0:1:255, default 32
control[2]: 0x980902  Saturation, 0:1:255, default 32
control[3]: 0x98090c  White Balance Temperature, Auto, 0:1:1, default 1
control[4]: 0x980913  Gain, 0:1:255, default 0
control[5]: 0x980918  Power Line Frequency, 0:1:2, default 2
control[6]: 0x98091a  White Balance Temperature, 0:10:10000, default 4000
control[7]: 0x98091b  Sharpness, 0:1:255, default 224
control[8]: 0x98091c  Backlight Compensation, 0:1:2, default 1
control[9]: 0x9a0901  Exposure, Auto, 0:1:3, default 3
control[10]: 0x9a0902  Exposure (Absolute), 1:1:10000, default 166
control[11]: 0x9a0903  Exposure, Auto Priority, 0:1:1, default 0
control[12]: 0x9a0904  Pan (relative), -4480:1:4480, default 0
control[13]: 0x9a0905  Tilt (relative), -1920:1:1920, default 0
control[14]: 0x9a0906  Pan Reset, 0:1:1, default 1
control[15]: 0x9a0907  Tilt Reset, 0:0:1, default 0
control[16]: 0xa046d03  Pan/tilt Reset, 0:1:3, default 1
control[17]: 0xa046d04  Focus (absolute), 0:1:255, default 0
control[18]: 0xa046d05  LED1 Mode, 0:1:132, default 0
control[19]: 0xa046d06  LED1 Frequency, 0:1:255, default 0
control[20]: 0xa046d71  Disable video processing, 0:1:1, default 0
control[21]: 0xa046d72  Raw bits per pixel, 0:1:1, default 0
resolutions of 2º format=8 
frame rates of 5º resolution=6 
Def. Res: 4  numb. fps:6
--------------------------------------- device #0
Name                     = HDA Intel: ALC663 Analog (hw:0,0)
Host API                 = ALSA
Max inputs = 2, Max outputs = 4
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #1
Name                     = HDA Intel: ALC663 Digital (hw:0,1)
Host API                 = ALSA
Max inputs = 0, Max outputs = 2
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #2
Name                     = USB Device 0x46d:0x994: USB Audio (hw:1,0)
Host API                 = ALSA
Max inputs = 1, Max outputs = 0
Def. low input latency   =    0.032
Def. low output latency  =   -1.000
Def. high input latency  =    0.128
Def. high output latency =   -1.000
Def. sample rate         = 16000.00
--------------------------------------- device #3
Name                     = front
Host API                 = ALSA
Max inputs = 0, Max outputs = 4
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #4
Name                     = surround40
Host API                 = ALSA
Max inputs = 0, Max outputs = 4
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #5
Name                     = surround51
Host API                 = ALSA
Max inputs = 0, Max outputs = 4
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #6
Name                     = surround71
Host API                 = ALSA
Max inputs = 0, Max outputs = 4
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #7
Name                     = iec958
Host API                 = ALSA
Max inputs = 0, Max outputs = 2
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #8
Name                     = spdif
Host API                 = ALSA
Max inputs = 0, Max outputs = 2
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #9
Name                     = pulse
Host API                 = ALSA
Max inputs = 32, Max outputs = 32
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #10
Name                     = dmix
Host API                 = ALSA
Max inputs = 0, Max outputs = 2
Def. low input latency   =   -1.000
Def. low output latency  =    0.043
Def. high input latency  =   -1.000
Def. high output latency =    0.043
Def. sample rate         = 48000.00
--------------------------------------- device #11
[ Default Input, Default Output ]
Name                     = default
Host API                 = ALSA
Max inputs = 32, Max outputs = 32
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #12
[ Default OSS Input, Default OSS Output ]
Name                     = /dev/dsp
Host API                 = OSS
Max inputs = 16, Max outputs = 16
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #13
Name                     = /dev/dsp1
Host API                 = OSS
Max inputs = 16, Max outputs = 0
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
----------------------------------------------
SampleRate:44100 Channels:2
Video driver: x11
A window manager is available


```

---

### Post by Kat of Zion on 2011-01-21
Been doing more tinkering around with different things.  Looks like one of the updates anywhere from 2 weeks ago to now is probably what did it, but I also think that Adobe's failure to really get in on 64-bit Linux is part of it.  

So, here are the 2 cams I use: UVC 1.3 cam (built in, mounted on my laptop's monitor) & the [Logitech Quickcam Orbit AF]("http://www.logitech.com/en-us/38/3480#section=specs")

Im attaching a few screencaps from various websites accessed in Google Chrome. To verify, I am using Flash Player version 10.1 r102.  Of all of these, the gtalk screencap is the only one that seems to show the image without all that pixelation.  I had my friend (who I Gtalked) with send me a screencap from their end and the image is the same as gtalk.jpg provided here.  Crystal clear.

---

### Post by Kat of Zion on 2011-01-23
Update:  I have tried flashplugin-installer in the following versions:

10.3.161.23-(sevenmachines1_amd64)
10.3.161.29-(sevenmachines1_amd64)
10.1.102.65

All produce the same pixely quality when using my webcams through a flash chatroom.  Google Talk (which is on its own tech) continues to shine as giving viewers the clearest picture.

---

