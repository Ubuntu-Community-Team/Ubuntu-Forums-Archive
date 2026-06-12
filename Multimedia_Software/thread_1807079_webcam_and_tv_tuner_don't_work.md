---
title: "webcam and tv tuner don't work"
date: 2011-07-18
forum: Multimedia Software
---

### Post by someitalian123 on 2011-07-18
My tv tuners works under vlc only, my webcam only works in vlc and xaw tv, I tried skype and it didn't detect either one. However in Puppy Linux both of these worked flawlessly, they were both detected in skype.  here's v4l-info.

```
### v4l2 device info [/dev/video0] ###
general info
    VIDIOC_QUERYCAP
    driver                  : "uvcvideo"
    card                    : "UVC Camera (046d:0819)"
    bus_info                : "usb-0000:00:1d.7-1"
    version                 : 1.0.0
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
    VIDIOC_ENUM_FMT(1,VIDEO_CAPTURE)
    index                   : 1
    type                    : VIDEO_CAPTURE
    flags                   : 1
    description             : "MJPEG"
    pixelformat             : 0x47504a4d [MJPG]
    VIDIOC_G_FMT(VIDEO_CAPTURE)
    type                    : VIDEO_CAPTURE
    fmt.pix.width           : 640
    fmt.pix.height          : 480
    fmt.pix.pixelformat     : 0x56595559 [YUYV]
    fmt.pix.field           : NONE
    fmt.pix.bytesperline    : 1280
    fmt.pix.sizeimage       : 614400
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

### v4l2 device info [/dev/video1] ###
general info
    VIDIOC_QUERYCAP
    driver                  : "cx8800"
    card                    : "ASUS PVR-416"
    bus_info                : "PCI:0000:02:04.0"
    version                 : 0.0.8
    capabilities            : 0x5010011 [VIDEO_CAPTURE,VBI_CAPTURE,TUNER,READWRITE,STREAMING]

standards
    VIDIOC_ENUMSTD(0)
    index                   : 0
    id                      : 0x1000 [NTSC_M]
    name                    : "NTSC-M"
    frameperiod.numerator   : 1001
    frameperiod.denominator : 30000
    framelines              : 525
    VIDIOC_ENUMSTD(1)
    index                   : 1
    id                      : 0x2000 [NTSC_M_JP]
    name                    : "NTSC-M-JP"
    frameperiod.numerator   : 1001
    frameperiod.denominator : 30000
    framelines              : 525
    VIDIOC_ENUMSTD(2)
    index                   : 2
    id                      : 0x4000 [?]
    name                    : "NTSC-443"
    frameperiod.numerator   : 1001
    frameperiod.denominator : 30000
    framelines              : 525
    VIDIOC_ENUMSTD(3)
    index                   : 3
    id                      : 0x7 [PAL_B,PAL_B1,PAL_G]
    name                    : "PAL-BG"
    frameperiod.numerator   : 1
    frameperiod.denominator : 25
    framelines              : 625
    VIDIOC_ENUMSTD(4)
    index                   : 4
    id                      : 0x10 [PAL_I]
    name                    : "PAL-I"
    frameperiod.numerator   : 1
    frameperiod.denominator : 25
    framelines              : 625
    VIDIOC_ENUMSTD(5)
    index                   : 5
    id                      : 0xe0 [PAL_D,PAL_D1,PAL_K]
    name                    : "PAL-DK"
    frameperiod.numerator   : 1
    frameperiod.denominator : 25
    framelines              : 625
    VIDIOC_ENUMSTD(6)
    index                   : 6
    id                      : 0x100 [PAL_M]
    name                    : "PAL-M"
    frameperiod.numerator   : 1001
    frameperiod.denominator : 30000
    framelines              : 525
    VIDIOC_ENUMSTD(7)
    index                   : 7
    id                      : 0x200 [PAL_N]
    name                    : "PAL-N"
    frameperiod.numerator   : 1
    frameperiod.denominator : 25
    framelines              : 625
    VIDIOC_ENUMSTD(8)
    index                   : 8
    id                      : 0x400 [PAL_Nc]
    name                    : "PAL-Nc"
    frameperiod.numerator   : 1
    frameperiod.denominator : 25
    framelines              : 625
    VIDIOC_ENUMSTD(9)
    index                   : 9
    id                      : 0x800 [PAL_60]
    name                    : "PAL-60"
    frameperiod.numerator   : 1001
    frameperiod.denominator : 30000
    framelines              : 525
    VIDIOC_ENUMSTD(10)
    index                   : 10
    id                      : 0x10000 [SECAM_B]
    name                    : "SECAM-B"
    frameperiod.numerator   : 1
    frameperiod.denominator : 25
    framelines              : 625
    VIDIOC_ENUMSTD(11)
    index                   : 11
    id                      : 0x40000 [SECAM_G]
    name                    : "SECAM-G"
    frameperiod.numerator   : 1
    frameperiod.denominator : 25
    framelines              : 625
    VIDIOC_ENUMSTD(12)
    index                   : 12
    id                      : 0x80000 [SECAM_H]
    name                    : "SECAM-H"
    frameperiod.numerator   : 1
    frameperiod.denominator : 25
    framelines              : 625
    VIDIOC_ENUMSTD(13)
    index                   : 13
    id                      : 0x320000 [SECAM_D,SECAM_K,SECAM_K1]
    name                    : "SECAM-DK"
    frameperiod.numerator   : 1
    frameperiod.denominator : 25
    framelines              : 625
    VIDIOC_ENUMSTD(14)
    index                   : 14
    id                      : 0x400000 [SECAM_L]
    name                    : "SECAM-L"
    frameperiod.numerator   : 1
    frameperiod.denominator : 25
    framelines              : 625

inputs
    VIDIOC_ENUMINPUT(0)
    index                   : 0
    name                    : "Television"
    type                    : TUNER
    audioset                : 0
    tuner                   : 0
    std                     : 0x7f7ff7 [PAL_B,PAL_B1,PAL_G,PAL_I,PAL_D,PAL_D1,PAL_K,PAL_M,PAL_N,PAL_Nc,PAL_60,NTSC_M,NTSC_M_JP,?,SECAM_B,SECAM_D,SECAM_G,SECAM_H,SECAM_K,SECAM_K1,SECAM_L]
    status                  : 0x0 []
    VIDIOC_ENUMINPUT(1)
    index                   : 1
    name                    : "S-Video"
    type                    : CAMERA
    audioset                : 0
    tuner                   : 0
    std                     : 0x0 []
    status                  : 0x0 []

tuners
    VIDIOC_G_TUNER(0)
    index                   : 0
    name                    : "Television"
    type                    : ANALOG_TV
    capability              : 0x70 [STEREO,LANG2,LANG1]
    rangelow                : 0
    rangehigh               : 4294967295
    rxsubchans              : 0x1 [MONO]
    audmode                 : MONO
    signal                  : 0
    afc                     : 0

video capture
    VIDIOC_ENUM_FMT(0,VIDEO_CAPTURE)
    index                   : 0
    type                    : VIDEO_CAPTURE
    flags                   : 0
    description             : "8 bpp, gray"
    pixelformat             : 0x59455247 [GREY]
    VIDIOC_ENUM_FMT(1,VIDEO_CAPTURE)
    index                   : 1
    type                    : VIDEO_CAPTURE
    flags                   : 0
    description             : "15 bpp RGB, le"
    pixelformat             : 0x4f424752 [RGBO]
    VIDIOC_ENUM_FMT(2,VIDEO_CAPTURE)
    index                   : 2
    type                    : VIDEO_CAPTURE
    flags                   : 0
    description             : "15 bpp RGB, be"
    pixelformat             : 0x51424752 [RGBQ]
    VIDIOC_ENUM_FMT(3,VIDEO_CAPTURE)
    index                   : 3
    type                    : VIDEO_CAPTURE
    flags                   : 0
    description             : "16 bpp RGB, le"
    pixelformat             : 0x50424752 [RGBP]
    VIDIOC_ENUM_FMT(4,VIDEO_CAPTURE)
    index                   : 4
    type                    : VIDEO_CAPTURE
    flags                   : 0
    description             : "16 bpp RGB, be"
    pixelformat             : 0x52424752 [RGBR]
    VIDIOC_ENUM_FMT(5,VIDEO_CAPTURE)
    index                   : 5
    type                    : VIDEO_CAPTURE
    flags                   : 0
    description             : "24 bpp RGB, le"
    pixelformat             : 0x33524742 [BGR3]
    VIDIOC_ENUM_FMT(6,VIDEO_CAPTURE)
    index                   : 6
    type                    : VIDEO_CAPTURE
    flags                   : 0
    description             : "32 bpp RGB, le"
    pixelformat             : 0x34524742 [BGR4]
    VIDIOC_ENUM_FMT(7,VIDEO_CAPTURE)
    index                   : 7
    type                    : VIDEO_CAPTURE
    flags                   : 0
    description             : "32 bpp RGB, be"
    pixelformat             : 0x34424752 [RGB4]
    VIDIOC_ENUM_FMT(8,VIDEO_CAPTURE)
    index                   : 8
    type                    : VIDEO_CAPTURE
    flags                   : 0
    description             : "4:2:2, packed, YUYV"
    pixelformat             : 0x56595559 [YUYV]
    VIDIOC_ENUM_FMT(9,VIDEO_CAPTURE)
    index                   : 9
    type                    : VIDEO_CAPTURE
    flags                   : 0
    description             : "4:2:2, packed, UYVY"
    pixelformat             : 0x59565955 [UYVY]
    VIDIOC_G_FMT(VIDEO_CAPTURE)
    type                    : VIDEO_CAPTURE
    fmt.pix.width           : 320
    fmt.pix.height          : 240
    fmt.pix.pixelformat     : 0x33524742 [BGR3]
    fmt.pix.field           : INTERLACED
    fmt.pix.bytesperline    : 960
    fmt.pix.sizeimage       : 230400
    fmt.pix.colorspace      : unknown
    fmt.pix.priv            : 0

vbi capture
    VIDIOC_G_FMT(VBI_CAPTURE)
    type                    : VBI_CAPTURE
    fmt.vbi.sampling_rate   : 28636363
    fmt.vbi.offset          : 244
    fmt.vbi.samples_per_line: 2048
    fmt.vbi.sample_format   : 0x59455247 [GREY]
    fmt.vbi.start[0]        : 10
    fmt.vbi.start[1]        : 273
    fmt.vbi.count[0]        : 17
    fmt.vbi.count[1]        : 17
    fmt.vbi.flags           : 0

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
    default_value           : 63
    flags                   : 0
    VIDIOC_QUERYCTRL(BASE+2)
    id                      : 9963778
    type                    : INTEGER
    name                    : "Saturation"
    minimum                 : 0
    maximum                 : 255
    step                    : 1
    default_value           : 127
    flags                   : 0
    VIDIOC_QUERYCTRL(BASE+3)
    id                      : 9963779
    type                    : INTEGER
    name                    : "Hue"
    minimum                 : 0
    maximum                 : 255
    step                    : 1
    default_value           : 127
    flags                   : 0


```There is also a /dev/video2 but when I try v4l-info /dev/video2 the terminal hangs and I have to close it out. Also I've tried. 
```

LD_PRELOAD=/usr/lib/libv4l/*v4l2convert*.so skype 

``` It didn't work. Also gstreamer-properties doesn't start. I don't know if it's related or not. I'm having a lot of problems with ubuntu on this pc. The first was that I couldn't even get it to boot off of the cd in order to install it, I had to use a usb.

---

### Post by someitalian123 on 2011-07-19
Bump,

Seriously somebody has to know how to fix this. It worked perfectly in puppy linux so it should work the same in ubuntu. I can post any logs or terminal output that you need just tell me what i need to do.

---

