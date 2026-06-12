---
title: "Quickcam Pro 9000 ISSUES"
date: 2007-12-13
forum: Multimedia &amp; Video
---

### Post by asnd16 on 2007-12-13
v4l-info

### v4l2 device info [/dev/video0] ###
general info
    VIDIOC_QUERYCAP
        driver                  : "uvcvideo"
        card                    : "UVC Camera (046d:0990)"
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
        fmt.pix.width           : 352
        fmt.pix.height          : 288
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
    VIDIOC_QUERYCTRL(PRIVATE_BASE+0)
        id                      : 134217728
        type                    : INTEGER
        name                    : "Backlight Compensation"
        minimum                 : 0
        maximum                 : 2
        step                    : 1
        default_value           : 1
        flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+1)
        id                      : 134217729
        type                    : MENU
        name                    : "Power Line Frequency"
        minimum                 : 0
        maximum                 : 2
        step                    : 1
        default_value           : 2
        flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+2)
        id                      : 134217730
        type                    : INTEGER
        name                    : "Sharpness"
        minimum                 : 0
        maximum                 : 255
        step                    : 1
        default_value           : 224
        flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+10)
        id                      : 134217738
        type                    : INTEGER
        name                    : "Exposure, Auto"
        minimum                 : 0
        maximum                 : 0
        step                    : 9
        default_value           : 8
        flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+11)
        id                      : 134217739
        type                    : INTEGER
        name                    : "Exposure (Absolute)"
        minimum                 : 1
        maximum                 : 10000
        step                    : 1
        default_value           : 166
        flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+12)
        id                      : 134217740
        type                    : BOOLEAN
        name                    : "White Balance Temperature, Auto"
        minimum                 : 0
        maximum                 : 0
        step                    : 0
        default_value           : 1
        flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+13)
        id                      : 134217741
        type                    : INTEGER
        name                    : "White Balance Temperature"
        minimum                 : 0
        maximum                 : 10000
        step                    : 10
        default_value           : 4000
        flags                   : 0

### video4linux device info [/dev/video0] ###
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
ioctl VIDIOCGCHAN: Invalid argument

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
        depth                   : 0
        palette                 : unknown

buffer
ioctl VIDIOCGFBUF: Invalid argument

window
    VIDIOCGWIN
        x                       : 0
        y                       : 0
        width                   : 352
        height                  : 288
        chromakey               : 0
        flags                   : 0

---

### Post by rsambuca on 2007-12-13
I would try installing the newest uvcvideo drivers.

---

