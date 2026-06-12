---
title: "Webcam Philips SPC525NC (SPC520NC)"
date: 2008-01-21
forum: Multimedia &amp; Video
---

### Post by felyduw on 2008-01-21
Hi

I've decided to try out the Philips SC520NC webcam (actually it's the SPC525NC because it has an included headset).

I'm running 7.10.

After connecting I ran lsusb and I got this:
```
Bus 004 Device 002: ID 0471:0334 Philips
```

As no /dev/video0 appeared I googled a bit and modprobed a recompiled from trunk UVC. At this time I got a /dev/video0 so I tried to run camorama and alas it failed.

Camorama on debug mode returned this:
```
VIDIOCGMBF  --  could not set buffer info, exiting...
```

v4l-info:
```
### v4l2 device info [/dev/video0] ###
general info
    VIDIOC_QUERYCAP
        driver                  : "uvcvideo"
        card                    : "USB Video Camera"
        bus_info                : "0000:00:1d.7"
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
        flags                   : 0
        description             : "YUV 4:2:2 (YUYV)"
        pixelformat             : 0x56595559 [YUYV]
    VIDIOC_G_FMT(VIDEO_CAPTURE)
        type                    : VIDEO_CAPTURE
        fmt.pix.width           : 320
        fmt.pix.height          : 240
        fmt.pix.pixelformat     : 0x56595559 [YUYV]
        fmt.pix.field           : NONE
        fmt.pix.bytesperline    : 640
        fmt.pix.sizeimage       : 153600
        fmt.pix.colorspace      : unknown
        fmt.pix.priv            : 0

controls
    VIDIOC_QUERYCTRL(BASE+0)
        id                      : 9963776
        type                    : INTEGER
        name                    : "Brightness"
        minimum                 : 0
        maximum                 : 37
        step                    : 1
        default_value           : 24
        flags                   : 0
    VIDIOC_QUERYCTRL(BASE+1)
        id                      : 9963777
        type                    : INTEGER
        name                    : "Contrast"
        minimum                 : 0
        maximum                 : 200
        step                    : 1
        default_value           : 124
        flags                   : 0
    VIDIOC_QUERYCTRL(BASE+2)
        id                      : 9963778
        type                    : INTEGER
        name                    : "Saturation"
        minimum                 : 0
        maximum                 : 200
        step                    : 1
        default_value           : 121
        flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+0)
        id                      : 134217728
        type                    : INTEGER
        name                    : "Backlight Compensation"
        minimum                 : 0
        maximum                 : 2
        step                    : 1
        default_value           : 0
        flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+1)
        id                      : 134217729
        type                    : MENU
        name                    : "Power Line Frequency"
        minimum                 : 0
        maximum                 : 2
        step                    : 1
        default_value           : 0
        flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+2)
        id                      : 134217730
        type                    : INTEGER
        name                    : "Sharpness"
        minimum                 : 0
        maximum                 : 63
        step                    : 1
        default_value           : 15
        flags                   : 0

### video4linux device info [/dev/video0] ###
general info
    VIDIOCGCAP
        name                    : "USB Video Camera"
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
        brightness              : 42509
        hue                     : 0
        colour                  : 39649
        contrast                : 40632
        whiteness               : 37137
        depth                   : 16
        palette                 : YUYV

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

I still don't see a light on the cam and I can't think of anything else at the moment. Does someone have some pointers to make this work?

Thanks.

Edit:
I tried to run Ekiga and it does stream some images but they're green.
So V4L2 works (barely), V4L doesn't.
Hope this helps.

---

### Post by Healey on 2008-06-21
Hi

Did you manage to get this to work on skype ???

I have purchased the Philips SPC520NC and wondered if you or anyone else could help.

I bought it because it was on a list that said it worked out of the box with Hardy

Thanks 

Healey

---

