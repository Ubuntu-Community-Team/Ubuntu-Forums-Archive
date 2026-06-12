---
title: "Strange webcam issue (it doesn't seem to work) Please assist"
date: 2008-08-22
forum: Multimedia Software
---

### Post by GeorgeIvanov on 2008-08-22
Alright so I have my little SiGma Micro USB Web Camera (Device ID: 1c4f:3000)

I tried using EasyCam, it found a driver, 'installed' it, and I tried to test it. Still nothing.

The device is recognized but it just doesn't work when I try to use it.
(For example, I plug it in, Cheese opens up by itself, no image/nothing)

I found this: [http://linux-uvc.berlios.de](http://linux-uvc.berlios.de)
I installed it, and tried again. Still nothing. (Well I might have installed it wrong since I am new to linux but I do not think so.. no errors came up)

I tried to open it with Camorama but this error came up:
```
Could not connect to video device (/dev/video0). Please check connection.
```

Now, naturally, after trying a lot of possible solutions out, I am pretty disappointed. 

Do any of you know why this is happening?

If so, I would greatly appreciate it if you can help me out.

Thank you in advance,
George.

---

### Post by GeorgeIvanov on 2008-08-22
EDIT:

Ok now the webcam works on Ekiga, but for some reason it has that same device connection error on Camorama and doesn't show up with Cheese.

Any suggestions?

---

### Post by GeorgeIvanov on 2008-08-23
Bump.

---

### Post by GeorgeIvanov on 2008-08-23
Ok here's what happens when I try to run it on Mencoder. (I tried it with both, V4L and V4L2 drivers.)

```
family@family-desktop:~$ mencoder tv:// -tv driver=v4l:width=320:height=240:device=/dev/webcam -ovc lavc -o webcam.avi
MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) D  CPU 2.66GHz (Family: 15, Model: 4, Stepping: 7)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l
 name: Video 4 Linux input
 author: Alex Beregszaszi
 comment: under development
=================================================================
 WARNING: YOU ARE USING V4L DEMUXER WITH V4L2 DRIVERS!!!
 As the V4L1 compatibility layer is broken, this may not work.
 If you encounter any problems, use driver=v4l2 instead.
 Bugreports on driver=v4l with v4l2 drivers will be ignored.
=================================================================
Selected device: USB Web Camera
 Capabilites: capture 
 Device type: 1
 Supported sizes: 48x32 => 640x480
 Inputs: 1
ioctl get channel failed: Invalid argument
ioctl set chan failed: Invalid argument
ioctl set chan failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
ioctl set picture failed: Invalid argument
The 'outfmt' of 'Planar YV12' is likely not supported by your card
Segmentation fault
family@family-desktop:~$ mencoder tv:// -tv driver=v4l2:width=320:height=240:device=/dev/webcam -ovc lavc -o webcam.avi
MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) D  CPU 2.66GHz (Family: 15, Model: 4, Stepping: 7)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: ioctl get standard failed: Invalid argument
Selected device: USB Web Camera
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: MJPEG
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
Audio block size too low, setting to 16384!
Floating point exception
family@family-desktop:~$ 

```

Oh right and the device is /webcam and not /video0.. but every time I try to run camorama for example, it tries to run video0..

I tried to test it with gstreamer-properties. I did it with both v4l and v4l2.

v4l: Device shows as 'USB Webcam' but this error message appears when I try to test it:
```
Video for Linux (v4l): Could not get/set settings from/on resource.
```

v4l2: Device shows as 'Unknown' and this error message appears:
```
Video for Linux 2 (v4l2): Failed getting controls attributes on device '/dev/video0.'
```

So yeah, so far, the only thing that shows/works with the webcam is still Ekiga.

---

### Post by GeorgeIvanov on 2008-08-24
Bump.

---

### Post by GeorgeIvanov on 2008-08-24
Bump.

---

### Post by GeorgeIvanov on 2008-08-24
Bump.

---

### Post by GeorgeIvanov on 2008-08-24
MORE INFO

This is the sudo lsusb -v output:

```

Bus 001 Device 007: ID 1c4f:3000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x1c4f 
  idProduct          0x3000 
  bcdDevice            1.00
  iManufacturer           1 SiGma Micro
  iProduct                2 USB Web Camera
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          342
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              250mA
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         0
      bInterfaceCount         2
      bFunctionClass         14 Video
      bFunctionSubClass       3 Video Interface Collection
      bFunctionProtocol       0 
      iFunction               2 USB Web Camera
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      1 Video Control
      bInterfaceProtocol      0 
      iInterface              2 USB Web Camera
      VideoControl Interface Descriptor:
        bLength                13
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdUVC               1.00
        wTotalLength           67
        dwClockFrequency       48.000000MHz
        bInCollection           1
        baInterfaceNr( 0)       1
      VideoControl Interface Descriptor:
        bLength                18
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Camera Sensor
        bAssocTerminal          0
        iTerminal               0 
        wObjectiveFocalLengthMin      0
        wObjectiveFocalLengthMax      0
        wOcularFocalLength            0
        bControlSize                  3
        bmControls           0x0004200a
          Auto-Exposure Mode
          Exposure Time (Absolute)
          Roll (Absolute)
          Privacy
      VideoControl Interface Descriptor:
        bLength                 8
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             2
        wTerminalType      0x0401 Composite Video
        bAssocTerminal          0
        iTerminal               0 
      VideoControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             3
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID               5
        iTerminal               0 
      VideoControl Interface Descriptor:
        bLength                 8
        bDescriptorType        36
        bDescriptorSubtype      4 (SELECTOR_UNIT)
        bUnitID                 4
        bNrInPins               2
        baSource( 0)            1
        baSource( 1)            2
        iSelector               0 
      VideoControl Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      5 (PROCESSING_UNIT)
      Warning: Descriptor too short
        bUnitID                 5
        bSourceID               4
        wMaxMultiplier          0
        bControlSize            2
        bmControls     0x0000163f
          Brightness
          Contrast
          Hue
          Saturation
          Sharpness
          Gamma
          Gain
          Power Line Frequency
          White Balance Temperature, Auto
        iProcessing             0 
        bmVideoStandards     0x 0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              32
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      VideoStreaming Interface Descriptor:
        bLength                            14
        bDescriptorType                    36
        bDescriptorSubtype                  1 (INPUT_HEADER)
        bNumFormats                        1
        wTotalLength                      145
        bEndPointAddress                  136
        bmInfo                              0
        bTerminalLink                       3
        bStillCaptureMethod                 2
        bTriggerSupport                     1
        bTriggerUsage                       0
        bControlSize                        1
        bmaControls( 0)                    11
      VideoStreaming Interface Descriptor:
        bLength                            11
        bDescriptorType                    36
        bDescriptorSubtype                  6 (FORMAT_MJPEG)
        bFormatIndex                        1
        bNumFrameDescriptors                3
        bFlags                             16
          Fixed-size samples: No
        bDefaultFrameIndex                  1
        bAspectRatioX                       0
        bAspectRatioY                       0
        bmInterlaceFlags                 0x00
          Interlaced stream or variable: No
          Fields per frame: 1 fields
          Field 1 first: No
          Field pattern: Field 1 only
          bCopyProtect                      0
      VideoStreaming Interface Descriptor:
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         1
        bmCapabilities                   0x03
          Still image supported
          Fixed frame-rate
        wWidth                            320
        wHeight                           240
        dwMinBitRate                  4915200
        dwMaxBitRate                  4915200
        dwMaxVideoFrameBufferSize      614400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  0
        dwMinFrameInterval             333333
        dwMaxFrameInterval             666666
        dwFrameIntervalStep            333333
      VideoStreaming Interface Descriptor:
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         2
        bmCapabilities                   0x03
          Still image supported
          Fixed frame-rate
        wWidth                            640
        wHeight                           480
        dwMinBitRate                  4915200
        dwMaxBitRate                  4915200
        dwMaxVideoFrameBufferSize      614400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  0
        dwMinFrameInterval             333333
        dwMaxFrameInterval             666666
        dwFrameIntervalStep            333333
      VideoStreaming Interface Descriptor:
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         3
        bmCapabilities                   0x03
          Still image supported
          Fixed frame-rate
        wWidth                            160
        wHeight                           120
        dwMinBitRate                  4915200
        dwMaxBitRate                  4915200
        dwMaxVideoFrameBufferSize      614400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  0
        dwMinFrameInterval             333333
        dwMaxFrameInterval             666666
        dwFrameIntervalStep            333333
      VideoStreaming Interface Descriptor:
        bLength                            19
        bDescriptorType                    36
        bDescriptorSubtype                  3 (STILL_IMAGE_FRAME)
        bEndpointAddress                    0
        bNumImageSizePatterns               3
        wWidth( 0)                        320
        wHeight( 0)                       240
        wWidth( 1)                        640
        wHeight( 1)                       480
        wWidth( 2)                        160
        wHeight( 2)                       120
        bNumCompressionPatterns             3
        bCompression( 0)                  128
      VideoStreaming Interface Descriptor:
        bLength                             6
        bDescriptorType                    36
        bDescriptorSubtype                 13 (COLORFORMAT)
        bColorPrimaries                     1 (BT.709,sRGB)
        bTransferCharacteristics            1 (BT.709)
        bMatrixCoefficients                 1 (BT.709)
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x025c  1x 604 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03bc  1x 956 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x024c  1x 588 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x02b0  1x 688 bytes
        bInterval               1
Device Status:     0x0000
  (Bus Powered)

```

The camera seems to be using the /dev/video0 and /dev/webcam devices (Because that's what shows up in the dev directory when I plug it in)

However, when I try sudo camorama --device /dev/camera0
or sudo camorama --device /dev/webcam
or sudo cheese --device /dev/camera0
or sudo cheese --device /dev/webcam

Nothing works.

The only thing that works is still Ekiga.

---

### Post by GeorgeIvanov on 2008-08-25
Bump.

---

### Post by untill on 2008-08-27
Yeah, same problem here, too.

[http://ubuntuforums.org/showthread.php?t=895612](http://ubuntuforums.org/showthread.php?t=895612)

Ekiga works, but neither Skype nor Cheese, Camorama, etc.

---

### Post by GeorgeIvanov on 2008-08-29
Alright, I tried everything, I even did a system re-install. I updated my UVC and still, Ekiga is the only thing that works.

After spending many hours getting Ubuntu on a [working] disk, and fixing all the stuff that didn't work, I'm pretty un-happy to see this happen.

Can anybody please finally help me?

I'm just going to have to go back to Windows if the things I need (For example, Webcam, Windows programs, etc.) do not work.

---

### Post by Crafty Kisses on 2008-08-30
You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2) if working with the settings does not work or help.
Post the results of the command > lsusb

---

