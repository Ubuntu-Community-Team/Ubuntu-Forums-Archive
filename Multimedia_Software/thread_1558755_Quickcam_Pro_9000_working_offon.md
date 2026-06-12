---
title: "Quickcam Pro 9000 working off/on"
date: 2010-08-22
forum: Multimedia Software
---

### Post by Kevin_E on 2010-08-22
Ubuntu 9.10
Quickcam Pro 9000
Logitech USB Headphones

(lsmod | grep video) command
```
uvcvideo               59080  1 
videodev               36736  2 uvcvideo
v4l1_compat            14336  2 uvcvideo,videodev

```(rmmod -f uvcvideo && sudo modprobe uvcvideo) command
```
ERROR: Removing 'uvcvideo': Resource temporarily unavailable

```Since 8.10, I've had issue trying to get my cam to work at all times.  But, it only does it when it wants to.  I don't know what is triggering it on, nor off.

With Cheese, at times it will detect the camera.  I'll shut down Cheese.  Bring it back up, and lo'n'behold, nothing is detected, and all I get are the rainbow color swatches and a block of snow on the bottom right-hand corner.  If happens to come on, some times I'll have sound, most of the time I won't.

For testing purposes, Youtube, there will be most times that it will detect it, and times that it won't.  When it does, I'll have sound.

I've recently learned of two other "capture devices" if they are called such (because when Cheese or any other proggie does work, the fps are very very lagging).   guvcview and luvcview.

guvcview
pop-up window read
```
Guvcview error:

Unable to open device
Please make sure the camera is connected
and that the linux-UVC driver is installed.
```And in terminal
```
guvcview 1.1.1
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
video device: /dev/video0 
/dev/video1 - device 1
ERROR opening V4L interface for /dev/video0
ERROR opening V4L interface: No such device
Init video returned -1

```luvcview
```
luvcview 0.2.4

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
ERROR opening V4L interface: No such device

```I'm driven quite insane on why nothing is either working or teasing me.  I DO NOT want to record on Windows.  I have a lag problem with fps there, anway.  Seems like guvcview is my best option, but I can't get it to detect anything.

For two years... what in the heck am I doing wrong?

Anymore info, tag me.

Thanks in advance for all replies.

---

### Post by no2498 on 2010-08-23
if the cam did not work well in windows
it may be a bad cam

but look in the cheese help files faq's

---

### Post by Kevin_E on 2010-08-23
Nah.  I know it's not a bad cam.  It just lags on Windows, using Logitech's software.  I've heard that's normal (something about it doing 15fps instead of 30, which others have mentioned getting 30fps in Windows Movie Maker).

I have read the FAQ thoroughly for Cheese.  This wouldn't, however, help me figure out the overall issue of its work/don't work actions, and it has never been picked up by guvcview and luvcview.

Connecting under Windows, I have absolutely no issue using it whenever and however (despite fps).  No matter what, it was identified and usable.

---

### Post by no2498 on 2010-08-23
this helps

5.1.&#8195;The video is sluggish/has a slow response. What can I do?


You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
This means, that your cpu is doing all the work. Change it to "xvimagesink"
("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.



To change the settings, run "gstreamer-properties", click the Video tab
and change the appropriate settings.



5.7.&#8195;Which cameras are supported


      Cheese uses gstreamer for video grabbing. So in principle Cheese supports 
      any camera that works with GStreamer. In principle that should be any camera
      which support video4linux or video4linux2.

---

### Post by no2498 on 2010-08-24
btw this program works for me if cheese dont. wxcam

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

---

### Post by Kevin_E on 2010-08-25
Thanks, no2498.  I've tried that first posting you placed before placing this topic, and it didn't make a difference.  :(

I will look into wxcam.  Will post back with my findings.

---

### Post by no2498 on 2010-08-25
read and install all the page tells you to

hope it works for you

---

### Post by maplegate on 2010-08-25
I have the same device and almost the same trouble.  

For me, cheese always finds the camera, but Skype has issues.  No big deal for me.

But sound is a problem.  What I have found invariably when the audio is not working is that under "System..Preferences..Sound" the input device has gotten toggled back to "internal" instead of the "0809 Audio".

Is there any way to force Ubuntu 10.04 to always use the device I tell it to use?

---

### Post by Rumpty on 2010-08-26
Kevin_E, for what it's worth, I have the Logitech Pro 9000 working in Ubuntu 9.10.

Running guvcview in the terminal-

guvcview 1.1.1
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
video device: /dev/video0 
/dev/video0 - device 1
Init. UVC Camera (046d:0990) (location: usb-0000:00:0b.1-2)

I see that /dev/video0 - device 1, whereas in yours /dev/video1 - device 1, which doesn't add up, looking at the previous line.

---

### Post by Kevin_E on 2010-08-26
**sigh**
I swear, I'm giving up.

I tried all options under wxcam, and each time I error-out.  Here's what it says with defaults set (auto):

Pop-up
```
An error has occured during frame capture.
Please check the "frame format" options in the preferences menu.
```Terminal
```
Determining video4linux API version...
Using video4linux 2 API
VIDIOC_ENUM_FRAMESIZES: Invalid argument
Resolution setted to 0x0
V4L2_CID_GAMMA is not supported
Determining pixel format...
pixel format: MJPEG
Found V4L2_PIX_FMT_MJPEG pixel format
pixel format: YUV 4:2:2 (YUYV)
Found V4L2_PIX_FMT_YUYV pixel format
VIDIOC_S_FMT: Device or resource busy
Device not mapped

```And thank you, Rumpty, for pointing out,
> I see that /dev/video0 - device 1, whereas in yours /dev/video1 - device 1, which doesn't add up, looking at the previous line.     How do I go about fixing that?  Heck... how do I start from ground zero??  This has become ridiculous.  Only me. :D

My cam options, however, under wxcam, was /dev/video0 and nothing else.  I even fiddled with the driver setting, switching from AUTO, VIDEO4LINUX1 and 2.  Under default, as you can read, it uses/detects V4L2.  Switching it to V4L1, I get the same pop-up and

```
Using video4linux 1 API
Resolution setted to 0x0
Determining palette format...
Error getting frame format
read: No such device

```


When do I get the thermite to destroy this beast?

---

### Post by Kevin_E on 2010-08-26
Here's something I've found while playing with kdenlive.  Anything out of the ordinary found here?

It, too, is saying there is no such device.  Funny, considering that Cheese (my default webcam thingee-mah-jig) ALWAYS pops up whenever the cam is unplugged then replugged, only to give me the majority of the time the color bars with static pic-in-pic on the bottom right corner.

Where's my happy pills..... :cry:

---

### Post by Kevin_E on 2010-08-29
Here's some more info as I was tinkering.

I done a "v4l-info /dev/video1" query and  got info.  Video0 does not pick up anything.

```
### v4l2 device info [/dev/video1] ###
general info
    VIDIOC_QUERYCAP
    driver                  : "uvcvideo"
    card                    : "UVC Camera (046d:0990)"
    bus_info                : "usb-0000:00:1a.7-3"
    version                 : 0.1.0
    capabilities            : 0x4000001 [VIDEO_CAPTURE,STREAMING]

standards

inputs
    VIDIOC_ENUMINPUT(0)
    index                   : 0
    name                    : "Camera 1"
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
    description             : "MJPEG"
    pixelformat             : 0x47504a4d [MJPG]
    VIDIOC_ENUM_FMT(1,VIDEO_CAPTURE)
    index                   : 1
    type                    : VIDEO_CAPTURE
    flags                   : 0
    description             : "YUV 4:2:2 (YUYV)"
    pixelformat             : 0x56595559 [YUYV]
    VIDIOC_G_FMT(VIDEO_CAPTURE)
    type                    : VIDEO_CAPTURE
    fmt.pix.width           : 1600
    fmt.pix.height          : 1200
    fmt.pix.pixelformat     : 0x56595559 [YUYV]
    fmt.pix.field           : NONE
    fmt.pix.bytesperline    : 3200
    fmt.pix.sizeimage       : 3840000
    fmt.pix.colorspace      : SRGB
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
    maximum                 : 255
    step                    : 1
    default_value           : 32
    flags                   : 0
    VIDIOC_QUERYCTRL(BASE+2)
    id                      : 9963778
    type                    : INTEGER
    name                    : "Saturation"
    minimum                 : 0
    maximum                 : 255
    step                    : 1
    default_value           : 32
    flags                   : 0

### video4linux device info [/dev/video1] ###
general info
    VIDIOCGCAP
    name                    : "UVC Camera (046d:0990)"
    type                    : 0x1 [CAPTURE]
    channels                : 1
    audios                  : 0
    maxwidth                : 960
    maxheight               : 720
    minwidth                : 48
    minheight               : 32

channels
    VIDIOCGCHAN(0)
    channel                 : 0
    name                    : "Camera 1"
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
    colour                  : 8224
    contrast                : 8224
    whiteness               : 0
    depth                   : 16
    palette                 : YUYV

buffer
ioctl VIDIOCGFBUF: Invalid argument

window
    VIDIOCGWIN
    x                       : 0
    y                       : 0
    width                   : 1600
    height                  : 1200
    chromakey               : 0
    flags                   : 0

```gstreamer-properties, with plugin libv4l2 chosen (v4l1, "No such device"), my device (now being picked-up), and "tested"
[COLOR=SeaGreen]pipeline "v4l2src device="/dev/video1"[/COLOR]
```
Oh for crying out loud, now it works.  Give me a moment.
It **WAS** giving me an error that it could not render 1600x1200.

```Will, after trying to duplicate my findings for this posting, stupid thing decided to TEMPORARILY work (hence title of this thread).  So, until next time.

Only Cheese lists video1.  All others lists video0 ("No such device").  How in the world do I change this so all proggies pick up video1?  In fact, how do I change ANY of the information given in the above "v4l-info /dev/video1"?

---

### Post by no2498 on 2010-08-30
you may try this for skype or change the name to what you need it to be


LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so any name you need it to be

---

### Post by Kevin_E on 2010-09-01
It appears that my reply was removed two days ago.

What I had stated was that it worked, then it just didn't... giving me a long continuous error message in which I had to use force to shut the app (Cheese) down.  Guvcview and luvcview wasn't able to pick up the cam with the supplied code because it was searching for video0.  Cheese initially worked, grabbing from video1, but later (and somehow) went looking for video0 and erroring (doesn't exist).  I can't replicate the results from two days ago because all I'm getting is the same errors referring to video0 not existing.

guvcview, currently:
popup
```
Guvcview error:

Unable to open device
Please make sure the camera is connected
and that the linux-UVC driver is installed.

```terminal:
```
guvcview 1.1.1
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Expression 'ioctl( devHandle, SNDCTL_DSP_CHANNELS, &temp )' failed in 'src/hostapi/oss/pa_unix_oss.c', line: 405
video device: /dev/video0 
/dev/video1 - device 1
ERROR opening V4L interface for /dev/video0
ERROR opening V4L interface: No such device
Init video returned -1
Terminated.

```Cheese, currently:
```
** (cheese:5583): WARNING **: Failed to open /dev/video0: No such device

```luvcview, currently:
```
luvcview 0.2.4

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
ERROR opening V4L interface: No such device

```:|
Yes, that's a look of discontent.

---

