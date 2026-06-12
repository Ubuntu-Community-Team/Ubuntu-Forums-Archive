---
title: "just got Logitech Quick Cam Pro 9000 what to do next?"
date: 2007-12-13
forum: Multimedia &amp; Video
---

### Post by asnd16 on 2007-12-13
Alright I just purchased the Logitech Quickcam Pro I am running gusty what should I do next. . .what are the best web cam programs?

---

### Post by asnd16 on 2007-12-13
all right I installed camorama and I get the error  could not connect to video device (/dev/video0). Please check connection.  easy cam is unable to connect to the cam as well

Here are my outputs 
> lsusb
Bus 005 Device 010: ID 046d:0990 Logitech, Inc. 
Bus 005 Device 007: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

>  ls -la /dev/video0
crw-rw---- 1 root video 81, 0 2007-12-13 12:39 /dev/video0


>  v4l-info

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

### Post by DaJL on 2007-12-16
I just got the same cam 5 minutes ago :p  and I'm running gutsy 64 bit.

I installed  luvcview  from "hard" and  I can record movies and take snapshot with it. 
you can download the package from here:
[http://packages.ubuntu.com/hardy/x11/luvcview](http://packages.ubuntu.com/hardy/x11/luvcview)
then to install:
sudo dpkg -i luvcview_20070512-3_amd64.deb

I then run it with:
luvcview -s 960x720


sound doesn't seem to work for now! 

it seems to work in kopete as well  at least  I see myself in the configuration panel.

---

### Post by asnd16 on 2007-12-16
here is what I got when trying that 
 luvcview -s 960x720
luvcview version 0.2.1 
 size width: 960 height: 720 
Video driver: x11
A window manager is available
video /dev/video0 
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  25
  Current serial number in output stream:  26

---

### Post by gubemton on 2007-12-23
You can make your computer a webcam server. I love "mjpg-streamer" and you can watch the video from all over the world (password protected).

[LIST]
[*]Download from [http://sourceforge.net/project/showfiles.php?group_id=206667](http://sourceforge.net/project/showfiles.php?group_id=206667)
[*]unpack with "tar xzvf mjpg_streamer_rev35.tgz"
[*]change to the directory "cd mjpg-streamer"
[*]build the programm "make clean all"
[*]copy files to the system "sudo cp *.so /usr/lib/"
[*]copy the programm itself "sudo cp mjpg-streamer /usr/bin"
[*]plug in your webcam and run the pogramm "mjpg_streamer -o "output_http.so -p 80""
[/LIST]

Have Fun!

---

### Post by Bossieman on 2008-01-02
Anyone managed to get michrophone to work?

---

