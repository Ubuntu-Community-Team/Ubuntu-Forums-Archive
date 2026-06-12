---
title: "guvcview crashes using logitech c525 webcam"
date: 2011-12-02
forum: Multimedia Software
---

### Post by aaronLund on 2011-12-02
guvcview just crashes when i open it.

It's version guvcview 1.4.3

Here's my verbose output:

```
aaron@ringo:/dev$ guvcview --verbose
guvcview 1.4.3
unexpected integer value (0) for vid_mux
Strings must be quoted
unexpected integer value (1) for snd_numsec
Strings must be quoted
unexpected integer value (160) for snd_bitrate
Strings must be quoted
unexpected integer value (2) for Pan_Step
Strings must be quoted
unexpected integer value (2) for Tilt_Step
Strings must be quoted
video_device: /dev/video0
vid_sleep: 0
cap_meth: 1
resolution: 640 x 480
windowsize: 480 x 700
vert pane: 0
spin behavior: 0
mode: mjpg
fps: 1/25
Display Fps: 0
bpp: 0
hwaccel: 1
avi_format: 0
sound: 1
sound Device: 0
sound samp rate: 0
sound Channels: 0
Sound delay: 0 nanosec
Sound Format: 80 
Pan Step: 2 degrees
Tilt Step: 2 degrees
Video Filter Flags: 0
image inc: 0
profile(default):/home/aaron/default.gpfl
starting portaudio...
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
language catalog=> dir:/usr/share/locale type:UTF-8 lang:en_US.UTF-8 cat:guvcview.mo
mjpg: setting format to 1196444237
capture method = 1
video device: /dev/video0 
Device Node Path: /dev/video0
  VID/PID: 046d 0826
  (null)
  HD Webcam C525
  serial: C562F6D0
Init. HD Webcam C525 (location: usb-0000:00:1f.2-1)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/15, 1/10, 2/15, 1/5, 
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 176 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 432, height = 240 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 544, height = 288 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 360 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 176 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 432, height = 240 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 544, height = 288 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 360 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 176 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 432, height = 240 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 544, height = 288 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 360 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 176 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 432, height = 240 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 544, height = 288 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 360 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 176 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 432, height = 240 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 544, height = 288 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 360 }
	Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
vid:046d 
pid:0826 
driver:uvcvideo
Adding control for Pan (relative)
UVCIOC_CTRL_ADD - Error: Operation not permitted
checking format: 1196444237
VIDIOC_G_COMP:: Invalid argument
   compression control not supported
fps is set to 1/24
drawing controls

control[0]: 0x9a0901  Exposure, Auto, 0:3:1, default 3
control[0]: 0x9a0902  Exposure (Absolute), 3:2047:1, default 166
control[0]: 0x9a0903  Exposure, Auto Priority, 0:1:1, default 0
control[0]: 0x9a090a  Focus (absolute), 0:255:5, default 60
control[0]: 0x9a090c  Focus, Auto, 0:1:1, default 1
control[0]: 0x9a090d  Zoom, Absolute, 1:5:1, default 1
resolutions of format(2) = 9 
frame rates of 1º resolution=7 
Def. Res: 0  numb. fps:7
--------------------------------------- device #0
Name                     = Intel 82801AA-ICH: Intel 82801AA-ICH (hw:0,0)
Host API                 = ALSA
Max inputs = 2, Max outputs = 2
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #1
Name                     = Intel 82801AA-ICH: Intel 82801AA-ICH - MIC ADC (hw:0,1)
Host API                 = ALSA
Max inputs = 2, Max outputs = 0
Def. low input latency   =    0.011
Def. low output latency  =   -1.000
Def. high input latency  =    0.043
Def. high output latency =   -1.000
Def. sample rate         = 48000.00
--------------------------------------- device #2
Name                     = HD Webcam C525: USB Audio (hw:1,0)
Host API                 = ALSA
Max inputs = 1, Max outputs = 0
Def. low input latency   =    0.011
Def. low output latency  =   -1.000
Def. high input latency  =    0.043
Def. high output latency =   -1.000
Def. sample rate         = 48000.00
--------------------------------------- device #3
Name                     = front
Host API                 = ALSA
Max inputs = 0, Max outputs = 2
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #4
Name                     = iec958
Host API                 = ALSA
Max inputs = 0, Max outputs = 2
Def. low input latency   =   -1.000
Def. low output latency  =    0.012
Def. high input latency  =   -1.000
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #5
Name                     = spdif
Host API                 = ALSA
Max inputs = 2, Max outputs = 2
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #6
Name                     = pulse
Host API                 = ALSA
Max inputs = 32, Max outputs = 32
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #7
Name                     = dmix
Host API                 = ALSA
Max inputs = 0, Max outputs = 2
Def. low input latency   =   -1.000
Def. low output latency  =    0.043
Def. high input latency  =   -1.000
Def. high output latency =    0.043
Def. sample rate         = 48000.00
--------------------------------------- device #8
[ Default Input, Default Output ]
Name                     = default
Host API                 = ALSA
Max inputs = 32, Max outputs = 32
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #9
[ Default OSS Input, Default OSS Output ]
Name                     = /dev/dsp
Host API                 = OSS
Max inputs = 16, Max outputs = 16
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
--------------------------------------- device #10
Name                     = /dev/dsp1
Host API                 = OSS
Max inputs = 16, Max outputs = 0
Def. low input latency   =    0.012
Def. low output latency  =    0.012
Def. high input latency  =    0.046
Def. high output latency =    0.046
Def. sample rate         = 44100.00
----------------------------------------------
SampleRate:0 Channels:0
no codec detected for ACC Low - (faac)
Video driver: x11
A window manager is available
(Desktop resolution = 1440x900)
Checking video mode 640x480@32bpp : OK 
recomended color depth = 16
The program 'guvcview' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 25 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Here's my lsusb:
```
aaron@ringo:/dev$ lsusb
Bus 001 Device 005: ID 046d:0826 Logitech, Inc. 
Bus 001 Device 003: ID 045e:0024 Microsoft Corp. Trackball Explorer
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
aaron@ringo:/dev$ 

```

uname:

```
aaron@ringo:/dev$ uname -a
Linux ringo 2.6.32-35-generic #78-Ubuntu SMP Tue Oct 11 15:27:15 UTC 2011 i686 GNU/Linux
aaron@ringo:/dev$ 

```

dmesg grepping for 'usb'
```
[    0.131911] usbcore: registered new interface driver usbfs
[    0.131954] usbcore: registered new interface driver hub
[    0.132088] usbcore: registered new device driver usb
[    0.441876] usb usb1: configuration #1 chosen from 1 choice
[    0.794859] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    1.146915] usb 1-1: configuration #1 chosen from 1 choice
[    1.260385] usb 1-2: new low speed USB device using uhci_hcd and address 3
[    1.441836] usb 1-2: configuration #1 chosen from 1 choice
[    1.979708] usbcore: registered new interface driver hiddev
[    1.995581] input: Microsoft Microsoft Trackball Explorer® as /devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2:1.0/input/input4
[    1.995910] generic-usb 0003:045E:0024.0001: input,hidraw0: USB HID v1.00 Mouse [Microsoft Microsoft Trackball Explorer®] on usb-0000:00:1f.2-2/input0
[    1.996002] usbcore: registered new interface driver usbhid
[    2.002584] usbhid: v2.6:USB HID core driver
[   33.584328] input: HD Webcam C525 as /devices/pci0000:00/0000:00:1f.2/usb1/1-1/1-1:1.2/input/input5
[   33.584952] usbcore: registered new interface driver uvcvideo
[   35.846993] usbcore: registered new interface driver snd-usb-audio
[   36.863355] usbcore: registered new interface driver ndiswrapper
[  296.760095] usb 1-1: USB disconnect, address 2
[  311.400104] usb 1-1: new full speed USB device using uhci_hcd and address 4
[  311.655362] usb 1-1: configuration #1 chosen from 1 choice
[  343.896106] usb 1-1: USB disconnect, address 4
[  352.080108] usb 1-2: USB disconnect, address 3
[  355.504089] usb 1-1: new low speed USB device using uhci_hcd and address 5
[  355.687626] usb 1-1: configuration #1 chosen from 1 choice
[  355.709690] input: Microsoft Microsoft Trackball Explorer® as /devices/pci0000:00/0000:00:1f.2/usb1/1-1/1-1:1.0/input/input6
[  355.710492] generic-usb 0003:045E:0024.0002: input,hidraw0: USB HID v1.00 Mouse [Microsoft Microsoft Trackball Explorer®] on usb-0000:00:1f.2-1/input0
[  397.704061] usb 1-2: new full speed USB device using uhci_hcd and address 6
[  398.000356] usb 1-2: configuration #1 chosen from 1 choice
[  398.338056] input: HD Webcam C525 as /devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2:1.2/input/input7

```

I'm using ndiswrapper for my wireless.  Could that have something to do with it?

---

### Post by no2498 on 2011-12-03
look in your system/preferences for multimedia systems selector click it open  click video change the plugin to something else
click the bottom to test your cam

---

### Post by aaronLund on 2011-12-03
Thanks for the reply. 

I think the issue was actually a bug with my crappy intel video card and X. 

I did a reinstall to 11.04 and all's well. 

This bug was also showing up: [http://ubuntuforums.org/showthread.php?t=1469981](http://ubuntuforums.org/showthread.php?t=1469981)

....so yeah. No bueno.

---

