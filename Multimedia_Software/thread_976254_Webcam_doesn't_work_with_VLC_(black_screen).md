---
title: "Webcam doesn't work with VLC (black screen)"
date: 2008-11-09
forum: Multimedia Software
---

### Post by RainCT on 2008-11-09
Manufacturer: PC Line
Model: PCL-W310
Detected as USB Camera 055f:d003 on /dev/video0
Driver: gspca_zc3xx

Hi,

I have the webcam described above and it works fine with cheese [SIZE="1"](except for video, but that seems to be a bug in cheese itself, and has already been reported on Launchpad by others)[/SIZE] and also with the test in gstreamer-properties (with v4l2).

However, I can't get it to work on VLC: if I tell it to open /dev/video0 as a capture device with v4l2 it starts counting the reproduction time but doesn't show anything at all, and if I change any of the settings (like the frame rate, which, by the way, is always 0.00 and if I change it sets itself back to that) VLC shows (on the command line) "v4l2 demux error: invalid tuner 0".

Some other applications (which are those that really interest me, VLC was just for testing) just display a black screen; this is the case of camstream, which just displays massive black on the input window and repeatedly prints the following error messages on the terminal: "W: VDLinux::run() VIDIOCMCAPTURE failed (Invalid argument)" and "W: run(): VIDIOCSYNC(1) failed (Invalid argument)". Another example is [tbeta](http://tbeta.nuigroup.com/), which also just displays a black screen and "FPS: 0", and touchlib.

Any idea?

---

### Post by RainCT on 2008-11-09
```

$ v4l-conf 
v4l-conf: using X11 display :0.0
dga: version 2.0
mode: 1440x900, depth=24, bpp=32, bpl=6400, base=0xe87e0000
/dev/video0 [v4l2]: no overlay support

```

```

$ v4l-info 

### v4l2 device info [/dev/video0] ###
general info
    VIDIOC_QUERYCAP
	driver                  : "zc3xx"
	card                    : "USB Camera (055f:d003)"
	bus_info                : "0000:00:1d.2"
	version                 : 2.2.0
	capabilities            : 0x5000001 [VIDEO_CAPTURE,READWRITE,STREAMING]

standards

inputs
    VIDIOC_ENUMINPUT(0)
	index                   : 0
	name                    : "zc3xx"
	type                    : CAMERA
	audioset                : 0
	tuner                   : 0
	std                     : 0x0 []
	status                  : 0x0 []

video capture
    VIDIOC_ENUM_FMT(0,VIDEO_CAPTURE)
	index                   : 0
	type                    : VIDEO_CAPTURE
	flags                   : 1
	description             : "JPEG"
	pixelformat             : 0x4745504a [JPEG]
    VIDIOC_G_FMT(VIDEO_CAPTURE)
	type                    : VIDEO_CAPTURE
	fmt.pix.width           : 640
	fmt.pix.height          : 480
	fmt.pix.pixelformat     : 0x4745504a [JPEG]
	fmt.pix.field           : NONE
	fmt.pix.bytesperline    : 640
	fmt.pix.sizeimage       : 115790
	fmt.pix.colorspace      : JPEG
	fmt.pix.priv            : 0

controls
    VIDIOC_QUERYCTRL(BASE+0)
	id                      : 9963776
	type                    : INTEGER
	name                    : "Brightness"
	minimum                 : 0
	maximum                 : 255
	step                    : 1
	default_value           : 128
	flags                   : 0
    VIDIOC_QUERYCTRL(BASE+1)
	id                      : 9963777
	type                    : INTEGER
	name                    : "Contrast"
	minimum                 : 0
	maximum                 : 256
	step                    : 1
	default_value           : 128
	flags                   : 0

### video4linux device info [/dev/video0] ###
general info
    VIDIOCGCAP
	name                    : "USB Camera (055f:d003)"
	type                    : 0x1 [CAPTURE]
	channels                : 1
	audios                  : 0
	maxwidth                : 640
	maxheight               : 480
	minwidth                : 48
	minheight               : 32

channels
    VIDIOCGCHAN(0)
	channel                 : 0
	name                    : "zc3xx"
	tuners                  : 0
	flags                   : 0x0 []
	type                    : CAMERA
	norm                    : 0

tuner
ioctl VIDIOCGTUNER: Invalid argument

audio
ioctl VIDIOCGAUDIO: Invalid argument

picture
    VIDIOCGPICT
	brightness              : 32896
	hue                     : 0
	colour                  : 0
	contrast                : 32768
	whiteness               : 39321
	depth                   : 8
	palette                 : unknown

buffer
ioctl VIDIOCGFBUF: Invalid argument

window
    VIDIOCGWIN
	x                       : 0
	y                       : 0
	width                   : 640
	height                  : 480
	chromakey               : 0
	flags                   : 0

```

```

$ dmesg | grep video
[    1.793898] pci 0000:00:02.0: Boot video device
[   39.328339] Linux video capture interface: v2.00

```

---

### Post by RainCT on 2008-11-09
More information: Ekiga and xawtv work fine.

```

$ xawtv -hwscan
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.27-7-generic)
looking for available devices
port 88-88
    type : Xvideo, image scaler
    name : Intel(R) Video Overlay

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : USB Camera (055f:d003)
    flags:  capture

```

---

### Post by RainCT on 2008-11-09
**Edit:** MEncoder does work, I was just using the wrong arguments. The following ones works:

```
mencoder tv:// -tv driver=v4l2:width=60:height=40:device=/dev/video0 -nosound -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi
```

------------------------------------------------------------------------------------

[size=1]Another application which doesn't seem to work is MEncoder:

```

$ mencoder tv:// -tv driver=v4l2:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp1:brightness=90:volume=35000 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi

MEncoder 2:1.0~rc2-0ubuntu17 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.30GHz (Family: 15, Model: 2, Stepping: 7)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: USB Camera (055f:d003)
 Capabilites:  video capture  read/write  streaming
 supported norms:
 inputs: 0 = zc3xx;
 Current input: 0
 Current format: unknown (0x4745504a)
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
Floating point exception

```[/size]

---

### Post by RainCT on 2008-11-10
Camstream works running it like this:

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camstream
```

So, the problem seems to be in tbeta and touchlib themselves.


**Edit:** I've opened a thread about this at the NUI Group's forum: [Webcam input is black with Tbeta and TouchLib in GNU/Linux](http://nuigroup.com/forums/viewthread/3502/).

---

### Post by riverfr0zen on 2008-11-11
I have pretty much the same problem that you describe. 

idVendor           0x041e Creative Technology, Ltd
idProduct          0x4036 Webcam Live!/Live! Pro

Testing on gstreamer-properties, and using cheese (even video) works fine.

But camstream and skype do not work. All I get is static, garbage from these programs. Camorama pops up the message "Unable to capture image" upon starting up, and promptly terminates.

Could it be because these apps don't support v4l2? I tried changing my input plugin to v4l, but the camera ends up not working at all then.

---

### Post by RainCT on 2008-11-11
> **riverfr0zen said:**
> But camstream and skype do not work. All I get is static, garbage from these programs. Camorama pops up the message "Unable to capture image" upon starting up, and promptly terminates.

Try to launch them like this:

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camstream
```

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

etc.

---

### Post by riverfr0zen on 2008-11-11
Looks like you were on the right path w/ the v4l1 preload - there is a bug report & discussion here:
[https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/291723](https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/291723)

VLC will actually work if you do the preload the way you mentioned (at least it did for me):
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so vlc

The catch comes if you are on a 64-bit system and are trying to run a 32-bit app. Then you have to follow proycon's workaround mentioned in the link above - for e.g. if you want to use a webcam with skype:

```
sudo apt-get install lib32v4l-0

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

```

I imagine you could do the same with tbeta, if your situation is the same (64-bit OS).

---

### Post by 4ebees on 2009-05-30
[QUOTE=riverfr0zen;6151598]"...LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
[/CODE]

And give this man an absolutely bloody huge Kewpie doll!

:popcorn:

Thanks for this. It was driving me to distraction.

---

