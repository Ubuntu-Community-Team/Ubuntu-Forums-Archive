---
title: "web cam help."
date: 2009-04-15
forum: Multimedia Software
---

### Post by LostMagix on 2009-04-15
Hello.

I have been tring to get a IBM Netcam working for a few days now with no luck but i think there may be a underlying problems, not just the driver.

I played around with the IBM cam for a while and ending up just giving up until I got a Logitech cam and it did the same as the netcam.

A few outputs to start off:


```
:~$ lsusb
Bus 001 Device 007: ID 046d:0870 Logitech, Inc. QuickCam Express
Bus 001 Device 006: ID 0545:8002 Xirlink, Inc. IBM NetCamera
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04b4:0033 Cypress Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

With both cams connected

```
:~$ ls /dev/video*
/dev/video0  /dev/video1
```


cat < /dev/video0 > foo.dat
cat < /dev/video1 > foo.dat 

no output at all.

The IBM cam, but not the logitech, in seen under camstream, here is the output:

```
:~$ camstream
W: CamStream version 0.27 starting.
>> void CCamStreamApp::ReadConfigFile()
<< void CCamStreamApp::ReadConfigFile()
D: CVideoCollector::VideoCollector()
D: >> CVideoDevice::CVideoDevice()
D: << CVideoDevice::CVideoDevice()
D: >> CVideoDeviceLinux::CVideoDeviceLinux(/dev/video0)
D: << CVideoDeviceLinux::CVideoDeviceLinux()
D: >> CVideoDeivceLinux::~CVideoDeviceLinux()
D: << CVideoDeivceLinux::~CVideoDeviceLinux()
D: >> CVideoDevice::~CVideoDevice()
D: << CVideoDevice::~CVideoDevice()
D: >> CVideoDevice::CVideoDevice()
D: << CVideoDevice::CVideoDevice()
D: >> CVideoDeviceLinux::CVideoDeviceLinux(/dev/video1)
D: << CVideoDeviceLinux::CVideoDeviceLinux()
>> CCamWindow::CCamWindow(QWidget*, const char*)
<< CCamWindow::CCamWindow(QWidget*, const char*)
>> CWebCamViewer::CWebCamViewer(CVideoDevice*, QWidget*, const char*)
  >> QDomNode CCamStreamApp::FindVideoDeviceConfig(const QString&, const QString&, bool)
    Trying to find video options for IBM USB Camera@/dev/video1
    D: Creating new node for IBM USB Camera@/dev/video1
  << QDomNode CCamStreamApp::FindVideoDeviceConfig(const QString&, const QString&, bool)
  >> CVideoOptions::CVideoOptions()
    >> virtual void CVideoOptions::DeclareVariables()
    << virtual void CVideoOptions::DeclareVariables()
  << CVideoOptions::CVideoOptions()
  D: CSnapshotSettingsDlg::CSnapshotSettingsDlg(...)
  W: QFont::setWeight: Value out of range (100)
  D: >> CVideoDeviceLinux::Init()
  W: Cannot query audio capabilities of video device.
  D: Using mmap(), size = 608256
  D: mmap()ed 2 buffers.
  W: Failed to restore image size (176, 144)
  D: Initial image size = (352, 288)
  D: << CVideoDeviceLinux::Init()
  D: CVideoSettingsDlg::SizeChanged(352x288)
  D: CVideoSettingsDlg::FramerateChanged(10)
  D: No Philips webcam detected, removing extension tab
  D: CCamPanel::SetSize(352x288)
  D: CCamPanel::SetImageSize(352x288)
  D: CCamPanel::SetVisibleSize(352x288)
  D: CCamPanel::SetSize(352x288)
  D: CCamPanel::SetImageSize(352x288)
  D: CCamPanel::SetVisibleSize(352x288)
  >> void CWebCamViewer::RecalcTotalViewSize()
  << void CWebCamViewer::RecalcTotalViewSize()
<< CWebCamViewer::CWebCamViewer(CVideoDevice*, QWidget*, const char*)
D: >> CVideoDevice::IncrementPalette(0)
D: >> CVideoDeviceLinux::StartCapture()
D: CVideoDeviceLinux::SetPalette picked palette 4 [rgb24]
D: >> CVideoDeviceLinux::CreateImagesRGB()
D: << CVideoDeviceLinux::CreateImagesRGB()
D: << CVideoDeviceLinux::StartCapture()
D: << CVideoDevice::IncrementPalette()
D: >> CVideoDeviceLinux::run()...

```


with the IBM:

```
:~$ v4l-conf
v4l-conf: using X11 display :0.0
dga: version 2.0
WARNING: No DGA direct video mode for this display.
mode: 1024x768, depth=24, bpp=32, bpl=4096, base=unknown
/dev/video0 [v4l2]: ioctl VIDIOC_QUERYCAP: Invalid argument
/dev/video0 [v4l]: no overlay support


:~$ sudo v4l-info

### video4linux device info [/dev/video0] ###
general info
    VIDIOCGCAP
	name                    : "IBM USB Camera"
	type                    : 0x1 [CAPTURE]
	channels                : 1
	audios                  : 0
	maxwidth                : 352
	maxheight               : 288
	minwidth                : 8
	minheight               : 4

channels
    VIDIOCGCHAN(0)
	channel                 : 0
	name                    : "Camera"
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
	brightness              : 32768
	hue                     : 32768
	colour                  : 32768
	contrast                : 49152
	whiteness               : 26880
	depth                   : 24
	palette                 : RGB24

buffer
    VIDIOCGFBUF
	base                    : (nil)
	height                  : 0
	width                   : 0
	depth                   : 0
	bytesperline            : 0

window
    VIDIOCGWIN
	x                       : 0
	y                       : 0
	width                   : 352
	height                  : 288
	chromakey               : 0
	flags                   : 4294967295



```


and with the logitech

```
v4l-conf
v4l-conf: using X11 display :0.0
dga: version 2.0
WARNING: No DGA direct video mode for this display.
mode: 1024x768, depth=24, bpp=32, bpl=4096, base=unknown
/dev/video0 [v4l2]: ioctl VIDIOC_QUERYCAP: Unknown error 515
/dev/video0 [v4l]: no overlay support

:~$ sudo v4l-info

### video4linux device info [/dev/video0] ###
general info
    VIDIOCGCAP
	name                    : "Logitech QuickCam USB"
	type                    : 0x0 []
	channels                : 1
	audios                  : 0
	maxwidth                : 352
	maxheight               : 292
	minwidth                : 32
	minheight               : 32

channels
    VIDIOCGCHAN(0)
	channel                 : 0
	name                    : "Camera"
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
	brightness              : 32768
	hue                     : 32768
	colour                  : 32768
	contrast                : 32768
	whiteness               : 32768
	depth                   : 24
	palette                 : RGB24

buffer
    VIDIOCGFBUF
	base                    : (nil)
	height                  : 0
	width                   : 0
	depth                   : 0
	bytesperline            : 0

window
    VIDIOCGWIN
	x                       : 0
	y                       : 0
	width                   : 352
	height                  : 292
	chromakey               : 0
	flags                   : 524288

```

What do you think?

---

### Post by jmore9 on 2009-04-20
I got my creative instant webcam working using this work around :

[https://answers.launchpad.net/ubuntu/+question/49739](https://answers.launchpad.net/ubuntu/+question/49739)

Maybe it could help you

---

