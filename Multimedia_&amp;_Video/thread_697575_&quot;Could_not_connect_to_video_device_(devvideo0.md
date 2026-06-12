---
title: "&quot;Could not connect to video device (/dev/video0)&quot;."
date: 2008-02-15
forum: Multimedia &amp; Video
---

### Post by DayOldPorridge on 2008-02-15
It's a Mikomi M6225, and I've already installed the right Linux drivers for it but whenever I plug it in, that's the message I get from Camorama.  And when I do lsusb, it seems that the webcam isn't being recognized at all:

> Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


I can plug in other USB devices without any problem, btw.

Any ideas on what I should do?

---

### Post by DayOldPorridge on 2008-02-15
Bump.

---

### Post by spamking2000 on 2008-02-15
Doing an lsusb doesn't always show everything... for example, right now I have a Logitech Web Cam, an HP All-in-one printer, and my Palm Pilot connected as well as cords that go to my Sansa and digital camera. When I do lsusb:

Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:2311 Hewlett-Packard 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

It shows a lot of options, but only 2 are actually listed with ID's.

One thing that I would recommend, you may have other Video inputs into your computer. I have an analog video capture card and a TV card in my machine in addition to the webcam plugged in USB.

you may need to start camorama using a different device. By default it will pull /dev/video0... for me that's my TV card. My webcam is on /dev/video2.

You can do this by going into terminal typing out:
camorama -d /dev/video1   or   camorama -d /dev/video2   etc... you get the idea.

Once you find the right one, just update the link in your applications menu so that it selects the right device.

---

### Post by DayOldPorridge on 2008-02-15
Hmm.. nope.  Tried all the way up to /dev/video10 but it still didn't recognize the camera.  Would it be worth noting that even when I try it with XP in VirtualBox it says that I don't have the right video capture hardware?

---

### Post by tutomlin on 2008-02-16
I have a similar problem, however my webcam (a logitech quickcam 5000) does show up under lsusb.  

In my case it seems to be installed properly, but for some reason xawtv and camorama don't open up properly.

If you have xawtv installed you should be able to use:
```
xawtv -hwscan
```
to see what devices are available.  In my case I get:
```

@hydra:~$ xawtv -hwscan
[: 12: (opcode:: unexpected operator
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-generic)
looking for available devices
port 280-311
    type : Xvideo, image scaler
    name : NV17 Video Texture

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : UVC Camera (046d:08ce)
    flags:  capture  
```

which as far as I can tell means that the kernel module is up and running and the webcam has been detected and set as the video0 device.  

another useful diagnostic command should be:
```
v4l -info
```
which should display information on any video4linux compatible webcams
in my case this looks like:


```
@hydra:~$ v4l-info

### v4l2 device info [/dev/video0] ###
general info
    VIDIOC_QUERYCAP
        driver                  : "uvcvideo"
        card                    : "UVC Camera (046d:08ce)"
        bus_info                : "0000:00:02.1"
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
        fmt.pix.width           : 320
        fmt.pix.height          : 240
        fmt.pix.pixelformat     : 0x47504a4d [MJPG]
        fmt.pix.field           : NONE
        fmt.pix.bytesperline    : 0
        fmt.pix.sizeimage       : 102400
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
        default_value           : 127
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

### video4linux device info [/dev/video0] ###
general info
    VIDIOCGCAP
        name                    : "UVC Camera (046d:08ce)"
        type                    : 0x1 [CAPTURE]
        channels                : 1
        audios                  : 0
        maxwidth                : 640
        maxheight               : 480
        minwidth                : 48
        minheight               : 32

channels
ioctl VIDIOCGCHAN: Invalid argument

tuner
ioctl VIDIOCGTUNER: Invalid argument

audio
ioctl VIDIOCGAUDIO: Invalid argument

picture
    VIDIOCGPICT
        brightness              : 32639
        hue                     : 0
        colour                  : 8224
        contrast                : 8224
        whiteness               : 0
        depth                   : 0
        palette                 : unknown

buffer
ioctl VIDIOCGFBUF: Invalid argument

window
    VIDIOCGWIN
        x                       : 0
        y                       : 0
        width                   : 320
        height                  : 240
        chromakey               : 0
        flags                   : 0


```

Hopefully this will help you diagnose your problem a little better.

I think my major problems are related to an error message I get when I use xawtv and v4l-conf:
```
@hydra:~$ v4l-conf
v4l-conf: using X11 display :0.0
dga: version 2.0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
```

I can get xawtv to load with the -nodga option:
```
@hydra:~$ xawtv -nodga

```
but it fails to capture video/ images from the camera with some fairly obtuse terminal messages.

I also tried camstream, which starts but gives an error 19 message when I try to load the camera

 I'm still stuck for now, but I'll update you if I get anywhere.  At any rate hopefully you can pick something useful from all my digging around:)

---

### Post by DayOldPorridge on 2008-02-16
Xaw doesn't seem to detect it either.  And just now when I tried to get the camera working with my XP partition, it also said "no video capture hardware", so it's not just Ubuntu or VirtualBox.  :/

---

### Post by tutomlin on 2008-02-16
sounds like you've got a problem with the camera, which is a bummer.  My last shot, if you haven't tried it already, would be to try a different USB slot since its possible you've just got one bad USB port.

---

### Post by DayOldPorridge on 2008-02-19
Yeah, already tried that.  I might just go end up buying another webcam that's been tested under Linux, but first I'll do some more searching to see if there might be a possible solution to this.

---

### Post by Ferrat on 2008-02-20
I have the exact same problem :/


Looked around a bit, it's a nVIDIA driver problem 
From nVIDIA FAW
> Why do applications that use DGA graphics fail?
	

The NVIDIA driver does not support the graphics component of the XFree86-DGA (Direct Graphics Access) extension. Applications can use the XDGASelectInput() function to acquire relative pointer motion, but graphics-related functions such as XDGASetMode() and XDGAOpenFramebuffer() will fail.

The graphics component of XFree86-DGA is not supported because it requires a CPU mapping of framebuffer memory. As graphics cards ship with increasing quantities of video memory, the NVIDIA X driver has had to switch to a more dynamic memory mapping scheme that is incompatible with DGA. Furthermore, DGA does not cooperate with other graphics rendering libraries such as Xlib and OpenGL because it accesses GPU resources directly.

NVIDIA recommends that applications use OpenGL or Xlib, rather than DGA, for graphics rendering. Using rendering libraries other than DGA will yield better performance and improve interoperability with other X applications.

---

