---
title: "problems getting xawtv, camorama and camstream to work with webcam"
date: 2008-02-18
forum: Multimedia &amp; Video
---

### Post by tutomlin on 2008-02-18
Hi all,

I have a Logitech quickcam pro 5000, usb webcam that I am trying to install and I'm stuck.  If you feel that I've missed a thread that covers my problem please let me know.

basically the webcam seems to be detected by the kernel and by the video4linux layer, but the interface programs like camorama, xawtv, camstream etc, don't seem to be able to talk to the camera properly.  I checked the program on a winxp box and the camera seems to be fine.  I also checked to make sure that my account is a member of the video group. 

The following document my diagnostic efforts:

when I connect the webcam it shows up fine with lsusb:
```
@hydra:~$ lsusb
Bus 002 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:08ce Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
```

Using xawtv -hwscan it looks like the webcam has been properly set up as /dev/video0:
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

video4linux also seems to be happy:
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

when I start xawtv, or use the v4l-conf call I get an error message about dga in xorg.  I can get xawtv to start with the -nodga option but the above error message still shows up, and I just get a blank window where I should be seeing the camera input. when I try to change the settings or capture an image I get and invalid argument  message:
```
@hydra:~$ xawtv -nodga
[: 12: (opcode:: unexpected operator
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-generic)
xinerama 0: 1920x1200+0+0
xinerama 1: 1600x1200+1920+0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_G_STD(std=0xb7d66450b7f66e73 [PAL_B,PAL_B1,PAL_I,PAL_D,PAL_D1,PAL_N,PAL_Nc,PAL_60,NTSC_M_JP,?,SECAM_D,SECAM_G,SECAM_K,SECAM_K1,SECAM_L,?ATSC_8_VSB,ATSC_16_VSB,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)]): Invalid argument
ioctl: VIDIOC_S_STD(std=0x0 []): Invalid argument
ioctl: VIDIOC_DQBUF(index=0;type=VIDEO_CAPTURE;bytesused=0;flags=0x0 [];field=ANY;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecode.minutes=0;timecode.hours=0;timecode.userbits="";sequence=0;memory=unknown): Invalid argument

```

cam stream starts with a no channel info warning, and when I try to open the viewer for the camera I get an error window titled "device error" that says: "The device experienced an error -19 (No such device). the window will be closed."  this closes the viewer window and leaves me in the main camstream window. (I did try to capture at a number of different resolutions but that doesn't seem to help)
```

@hydra:~$ camstream
CVideoDeviceInput: Warning: no channel info available.
CCamWindow::CCamWindow()
CWebCamViewer::CWebCamViewer(0x80d1898, 320x240)
CVideoDevice::Init()
Allocating own buffer.
Trying to find video options for UVC Camera (046d:08ce):/dev/video0
searching UVC Camera (046d:08ce)
CSnapshotSettingsDlg::CSnapshotSettingsDlg(...)
CVideoSettingsDlg::SizeChanged(352x288)
CVideoSettingsDlg::FramerateChanged(10)
CCamPanel::SetSize(352x288)
CCamPanel::SetImageSize(352x288)
CCamPanel::SetVisibleSize(352x288)
CVideoDevice::SetSize(320, 240)
SWIN: Input/output error
CCamPanel::SetSize(352x288)
CCamPanel::SetImageSize(352x288)
CCamPanel::SetVisibleSize(352x288)
CCamPanel::SetSize(352x288)
CCamPanel::SetImageSize(352x288)
CCamPanel::SetVisibleSize(352x288)
RecalcTotalViewSize: resize viewport(352x288)
EnableRGB: +
CVideoDevice::SetPalette picked palette 8 [yuyv]
CVideoDevice::CreateImagesRGB()
 allocating space for RGB
CVideoDevice::StartCapture() go!
CVideoDevice::LoadImage() Error loading image; errorcode=-19

EnableRGB: -
CVideoDevice::ResetImagesRGB()
 freeing memory
CVideoDevice::SetPalette picked palette 0 []
CVideoDevice::StopCapture() halt!
CWebCamViewer::~CWebCamViewer()
CWebCamViewer::StopTimeSnap()
CWebCamViewer::StopFTP()
CCamWindow::~CCamWindow()
```


Sorry for the lengthy post, I just don't want to get people barking up the wrong tree when I've already done the leg work.

Thanks

---

### Post by Forlornity on 2008-02-18
looks like a v4l2 device to me, and afaik camorama doesn't support v4l2, try opening it in Ekiga using v4l2.

-Forlornity

---

### Post by tutomlin on 2008-02-19
Thanks for the response

Trying your suggestion I had no luck, starting up I get a "failed to open the device" error, with the message: 
"your driver doesn't support any of the formats tried by Ekiga"

messing around with the settings in Ekiga I can get a similar message titled "Error while opeing video device UVC Camera (046d:08ce)"  with the message: 
"Your driver doesn't seem to support any of the color formats supported by Ekiga.
Please check your kernel driver documentation in order to determine which Palette is supported."

On a side note: My goal is to use this webcam to capture static images and short videos rather than using it in a live webcame type application.  I'm not sure that Ekiga is the right software for me.  On the otherhand I'm happy to try anything to identify the problem for the moment.

Thanks again for the help

---

### Post by tutomlin on 2008-02-19
On a side note I also tried the camera on a secondary system I have running Ubuntu, which uses an ATI video chipset rather than the Nvidia in my primary system.  This got rid of the DGA errors (apparently these are known bugs with the Nvidia proprietary drivers), but the software still can't connect to the quickcam properly.

---

### Post by wowtip on 2008-02-24
I am in the same position. Would also like to know if anyone knows how to get the cam working with xawtv / camstream (using a Logitech pro 9000).

One things you could try:
Do you get an image using luvcview? I do.
(sudo apt-get install luvcview)

I also managed to get it working with the Skype beta, but I still haven't figured out how to change the resolution to something better than 320x200.

---

### Post by tutomlin on 2008-02-26
For some reason I can't apt-get the luvcview package.

Following the directions here: [https://help.ubuntu.com/community/InstallingLogitechQuickcamPro5000OnEdgy](https://help.ubuntu.com/community/InstallingLogitechQuickcamPro5000OnEdgy)
and using the latest release version (luvcview-20070512) I get problems trying to install the package from source on the make command.  In short I can't check that one out because I can't get it installed.

Skype beta doesn't seem to detect the webcam automatically as the skype webpage claims it would.  Is there a manual way of making it use the webcam?

Seems like I may have a different problem (or at least an additional set of problems to go with this one  :)  )

---

### Post by tabotto on 2008-02-29
Exactly the same report, from kubuntu gutsy. My webcam is a logitech orbit. 

Somewhere else I've read that there could be a problem when multiple logitech devices (particular, mouse) are connected via USB.. but logitech mice is all I have.
Unfortunately can not try a PS/2 port (no port..). Is this also your experience ?

Any pointers would be very much appreciated.. thanks

---

### Post by tabotto on 2008-03-02
Finally got the see the cam using luvcview and the uvc driver. To compile luvcview
I somehow had to comment out #include "v4l2_enumfrmfmt.h" in frmfmtenum.c then
finally the sphere turned on. This was the MP model

I then found out there are problems with this cam chipset.
[http://www.quickcamteam.net/documentation/faq/logitech-webcam-linux-usb-incompatibilities]("http://www.quickcamteam.net/documentation/faq/logitech-webcam-linux-usb-incompatibilities")

The problem maybe solved with the upgraded model, Orbit AF
[http://www.quickcamteam.net/hcl/linux/logitech-webcams]("http://www.quickcamteam.net/hcl/linux/logitech-webcams")

while I ponder that decision, I got an RMA on my webcam. Still looking for the perfect one..

---

### Post by punong_bisyonaryo on 2008-03-05
In Ekiga, go to Edit > Preferences, and under the video settings set your webcam to use v4l2. If it works, it's because Ekiga defaults to v4l1 and other programs like cheese can only use v4l1.

This is a growing concern for me: [uvcvideo dropped support for v4l1]("http://antirez.com/m/p.php?i=169"), leaving a lot of webcam owners/software writers out cold with their v4l1-only software. Searching the forums, there's quite a number of people with uvcvideo webcams having these problems (like [this]("http://ubuntuforums.org/showthread.php?t=715366&highlight=uvcvideo") for example). I'm looking to petition those uvcvideo engineers about this "design" bug.

---

### Post by max littlemore on 2008-03-21
> **punong_bisyonaryo said:**
> In Ekiga, go to Edit > Preferences, and under the video settings set your webcam to use v4l2. If it works, it's because Ekiga defaults to v4l1 and other programs like cheese can only use v4l1.

This is a growing concern for me: [uvcvideo dropped support for v4l1]("http://antirez.com/m/p.php?i=169"), leaving a lot of webcam owners/software writers out cold with their v4l1-only software. Searching the forums, there's quite a number of people with uvcvideo webcams having these problems (like [this]("http://ubuntuforums.org/showthread.php?t=715366&highlight=uvcvideo") for example). I'm looking to petition those uvcvideo engineers about this "design" bug.

I'm a bit new to all this web cam stuff, but I have managed to get v4l2 working in cheese. To do this, run gstreamer-properties in a terminal and select "Video for Linux 2 (v4l2)" as the default input plugin on the Video tab.

This solution will probably solve the problem - given that cheese is good for video/still capture.

I agree it's a shame that support for v4l1 has been dropped, but I find it even more annoying that so much software doesn't abstraction for video input properly, meaning that camorama for example can't be configured to work with v4l2. My web cam only works with v4l2. Strikes me as a sensible design approach use gstreamer or such to provide abstraction and let users configure it easily through either command line or UI :confused:.

---

