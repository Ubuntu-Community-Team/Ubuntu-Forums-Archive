---
title: "Problem Skype (webcam) 20.04"
date: 2020-10-21
forum: Multimedia Software
---

### Post by ubontik22 on 2020-10-21
Hi everybody,

I updated 18.04 to 20.04 and Skype webcam stopped working.
The same problem with cheese and guvcview. There is a black screen for a second than it changes to white.

Thank you

```
$ lsusb
Bus 001 Device 008: ID 046d:0825 Logitech, Inc. Webcam C270
----------------
$ v4l2-ctl -d /dev/video0 --all
Driver Info:
    Driver name      : uvcvideo
    Card type        : UVC Camera (046d:0825)
    Bus info         : usb-0000:00:1a.0-1.3
    Driver version   : 5.4.65
    Capabilities     : 0x84a00001
        Video Capture
        Metadata Capture
        Streaming
        Extended Pix Format
        Device Capabilities
    Device Caps      : 0x04200001
        Video Capture
        Streaming
        Extended Pix Format
Media Driver Info:
    Driver name      : uvcvideo
    Model            : UVC Camera (046d:0825)
    Serial           : 0124EF00
    Bus info         : usb-0000:00:1a.0-1.3
    Media version    : 5.4.65
    Hardware revision: 0x00000012 (18)
    Driver version   : 5.4.65
Interface Info:
    ID               : 0x03000002
    Type             : V4L Video
Entity Info:
    ID               : 0x00000001 (1)
    Name             : UVC Camera (046d:0825)
    Function         : V4L2 I/O
    Flags         : default
    Pad 0x01000007   : 0: Sink
      Link 0x02000019: from remote pad 0x100000a of entity 'Extension 4': Data, Enabled, Immutable
Priority: 2
Video input : 0 (Camera 1: ok)
Format Video Capture:
    Width/Height      : 640/480
    Pixel Format      : 'MJPG' (Motion-JPEG)
    Field             : None
    Bytes per Line    : 0
    Size Image        : 302080
    Colorspace        : sRGB
    Transfer Function : Default (maps to sRGB)
    YCbCr/HSV Encoding: Default (maps to ITU-R 601)
    Quantization      : Default (maps to Full Range)
    Flags             : 
Crop Capability Video Capture:
    Bounds      : Left 0, Top 0, Width 640, Height 480
    Default     : Left 0, Top 0, Width 640, Height 480
    Pixel Aspect: 1/1
Selection Video Capture: crop_default, Left 0, Top 0, Width 640, Height 480, Flags: 
Selection Video Capture: crop_bounds, Left 0, Top 0, Width 640, Height 480, Flags: 
Streaming Parameters Video Capture:
    Capabilities     : timeperframe
    Frames per second: 25.000 (25/1)
    Read buffers     : 0# v4l2-ctl -d /dev/video0 --all
Driver Info:
    Driver name      : uvcvideo
    Card type        : UVC Camera (046d:0825)
    Bus info         : usb-0000:00:1a.0-1.3
    Driver version   : 5.4.65
    Capabilities     : 0x84a00001
        Video Capture
        Metadata Capture
        Streaming
        Extended Pix Format
        Device Capabilities
    Device Caps      : 0x04200001
        Video Capture
        Streaming
        Extended Pix Format
Media Driver Info:
    Driver name      : uvcvideo
    Model            : UVC Camera (046d:0825)
    Serial           : 0124EF00
    Bus info         : usb-0000:00:1a.0-1.3
    Media version    : 5.4.65
    Hardware revision: 0x00000012 (18)
    Driver version   : 5.4.65
Interface Info:
    ID               : 0x03000002
    Type             : V4L Video
Entity Info:
    ID               : 0x00000001 (1)
    Name             : UVC Camera (046d:0825)
    Function         : V4L2 I/O
    Flags         : default
    Pad 0x01000007   : 0: Sink
      Link 0x02000019: from remote pad 0x100000a of entity 'Extension 4': Data, Enabled, Immutable
Priority: 2
Video input : 0 (Camera 1: ok)
Format Video Capture:
    Width/Height      : 640/480
    Pixel Format      : 'MJPG' (Motion-JPEG)
    Field             : None
    Bytes per Line    : 0
    Size Image        : 302080
    Colorspace        : sRGB
    Transfer Function : Default (maps to sRGB)
    YCbCr/HSV Encoding: Default (maps to ITU-R 601)
    Quantization      : Default (maps to Full Range)
    Flags             : 
Crop Capability Video Capture:
    Bounds      : Left 0, Top 0, Width 640, Height 480
    Default     : Left 0, Top 0, Width 640, Height 480
    Pixel Aspect: 1/1
Selection Video Capture: crop_default, Left 0, Top 0, Width 640, Height 480, Flags: 
Selection Video Capture: crop_bounds, Left 0, Top 0, Width 640, Height 480, Flags: 
Streaming Parameters Video Capture:
    Capabilities     : timeperframe
    Frames per second: 25.000 (25/1)
    Read buffers     : 0
                     brightness 0x00980900 (int)    : min=0 max=255 step=1 default=128 value=128
                       contrast 0x00980901 (int)    : min=0 max=255 step=1 default=32 value=32
                     saturation 0x00980902 (int)    : min=0 max=255 step=1 default=32 value=32
 white_balance_temperature_auto 0x0098090c (bool)   : default=1 value=1
                           gain 0x00980913 (int)    : min=0 max=255 step=1 default=64 value=192
           power_line_frequency 0x00980918 (menu)   : min=0 max=2 default=2 value=2
                0: Disabled
                1: 50 Hz
                2: 60 Hz
      white_balance_temperature 0x0098091a (int)    : min=0 max=10000 step=10 default=4000 value=1070 flags=inactive
                      sharpness 0x0098091b (int)    : min=0 max=255 step=1 default=24 value=24
         backlight_compensation 0x0098091c (int)    : min=0 max=1 step=1 default=0 value=0
                  exposure_auto 0x009a0901 (menu)   : min=0 max=3 default=3 value=3
                1: Manual Mode
                3: Aperture Priority Mode
              exposure_absolute 0x009a0902 (int)    : min=1 max=10000 step=1 default=166 value=5 flags=inactive
         exposure_auto_priority 0x009a0903 (bool)   : default=0 value=1
                      led1_mode 0x0a046d05 (menu)   : min=0 max=3 default=3 value=3
                0: Off
                1: On
                2: Blink
                3: Auto
                 led1_frequency 0x0a046d06 (int)    : min=0 max=131 step=1 default=0 value=0

                     brightness 0x00980900 (int)    : min=0 max=255 step=1 default=128 value=128
                       contrast 0x00980901 (int)    : min=0 max=255 step=1 default=32 value=32
                     saturation 0x00980902 (int)    : min=0 max=255 step=1 default=32 value=32
 white_balance_temperature_auto 0x0098090c (bool)   : default=1 value=1
                           gain 0x00980913 (int)    : min=0 max=255 step=1 default=64 value=192
           power_line_frequency 0x00980918 (menu)   : min=0 max=2 default=2 value=2
                0: Disabled
                1: 50 Hz
                2: 60 Hz
      white_balance_temperature 0x0098091a (int)    : min=0 max=10000 step=10 default=4000 value=1070 flags=inactive
                      sharpness 0x0098091b (int)    : min=0 max=255 step=1 default=24 value=24
         backlight_compensation 0x0098091c (int)    : min=0 max=1 step=1 default=0 value=0
                  exposure_auto 0x009a0901 (menu)   : min=0 max=3 default=3 value=3
                1: Manual Mode
                3: Aperture Priority Mode
              exposure_absolute 0x009a0902 (int)    : min=1 max=10000 step=1 default=166 value=5 flags=inactive
         exposure_auto_priority 0x009a0903 (bool)   : default=0 value=1
                      led1_mode 0x0a046d05 (menu)   : min=0 max=3 default=3 value=3
                0: Off
                1: On
                2: Blink
                3: Auto
                 led1_frequency 0x0a046d06 (int)    : min=0 max=131 step=1 default=0 value=0



```

---

### Post by Autodave on 2020-10-22
Make a 20.04 install medium.  Boot to that and see if the camera works then.  Upgrading can often cause problems like you are having.  I learned a looong time ago to always do clean installs after backing up everything first.

If your camera works on the boot disk, your easiest fix may be to do a clean install after backing up your data.

---

### Post by ubontik22 on 2020-10-22
What is the MEDIUM? I installed from a USB drive.

---

### Post by ubontik22 on 2020-10-22
It works on other computer.

---

### Post by CelticWarrior on 2020-10-22
> [COLOR=#000000]What is the MEDIUM? I installed from a USB drive.[/COLOR]
> [COLOR=#000000]It works on other computer.[/COLOR]

Irrelevant.
Please try in a live session. Media doesn't matter as long as it boots.

---

### Post by ubontik22 on 2020-10-28
The camera is still not working...

---

