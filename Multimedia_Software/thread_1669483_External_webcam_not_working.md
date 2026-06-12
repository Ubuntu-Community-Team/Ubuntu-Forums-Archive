---
title: "External webcam not working"
date: 2011-01-17
forum: Multimedia Software
---

### Post by Jammanuser on 2011-01-17
I just recently purchased a [GTMax Flexible 12 Mega Pixel High Resolution w/ 4 LED Light & Microphone USB PC Webcam - Black]("http://www.amazon.com/GTMax-Flexible-Resolution-Microphone-Webcam/dp/B004AUSOOU/ref=sr_1_3?s=electronics&ie=UTF8&qid=1295308250&sr=1-3") from amazon.com, and attempted to use it in Ubuntu 8.10, but can't get it to work. The LEDs come on when I plug it into my laptop's usb port, but no video. I've tested it with Cheese Webcam Booth, and also an external website, but it doesn't work.

Of course, though, I'm not entirely sure its really the webcam, since Cheese Webcam Booth seems to be turning on my built-in laptop webcam which might be interfering with it, and also the tokbox widget in the website doesn't completely load anyway in ubuntu, webcam or no, so I'm thinking that maybe its only Cheese and tokbox which are not working.

My OS is Ubuntu 8.10 64 bit. Cheese Webcam Booth also does not work with my interal cam, though it turns it on, and I've confirmed it (i.e. cheese + internal webcam) does work in my ubuntu 9.10 32 bit which is installed in a multiboot on the same computer.

I would like to get these problems resolved, ASAP, as I need to have my webcam (at least one of them, preferably both) working in ubuntu 8.10, for that's the OS I use the most often.

I will note that my laptop is a Dell Studio 1535, and since I've installed Ubuntu 8.10 on it, I've had a number of other hardware issues with it on ubuntu, but I've been able to get most of them resolved a long time ago, but the webcam thing is one that I haven't got to work since I first installed ubuntu (which was God knows how long ago).

Thanks in advance, and if you need any more info, just ask.

---

### Post by no2498 on 2011-01-18
set the cam you like to use in gstreamer-properties
click video set it
try v4l and vyl2 use the bottom test button for each 1

---

### Post by Jammanuser on 2011-01-18
> **no2498 said:**
> set the cam you like to use in gstreamer-properties
click video set it
try v4l and vyl2 use the bottom test button for each 1
Hey, thanks. Doing what you said, with option Video for Linux (v4l) for Plugin and option USB2.0 PC CAMERA for Device, and pressing Test resulted in an error message:

> 
Video for Linux (v4l): Could not get/set settings from/on resource.

However, changing Plugin to Video for Linux (v4l2) and Integrated Webcam for Device, and pressing Test, resulted in it turning the integrated webcam on, and displaying the video from on it on the screen, however, how do I get it to work where I can actually use it for something?

Also, I would like to get the external webcam working.

Thanks.

EDIT: Nevermind for the first thing. I confirmed that my internal webcam is working at testmycam.com. However, I still would like to get my external webcam to work, like already mentioned.

EDIT again: Looks like I spoke too soon. I unplugged my external webcam, and now my internal webcam is neither working at testmycam.com, nor is it working through the use of the Test button and settings like mentioned above for the integrated webcam. When I go to testmycam.com with my external webcam unplugged, it just shows what's shown in my attached screenshot, and when I go to gstreamer-properties, set the settings to those appropriate for the integrated webcam, press Test, it says the following:

> 
Video for Linux 2 (v4l2): Device '/dev/video0' cannot capture at 1600x1200


and my Terminal window shows this:

> 
 gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
libv4l2: error setting pixformat: Device or resource busy
libv4l2: error requesting 4 buffers: Device or resource busy
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Device '/dev/video0' cannot capture at 1600x1200 [v4l2src_calls.c(1289): gst_v4l2src_set_capture (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src5:
Call to S_FMT failed for YU12 @ 1600x1200: Device or resource busy]
libv4l2: error setting pixformat: Device or resource busy
libv4l2: error requesting 4 buffers: Device or resource busy
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Device '/dev/video0' cannot capture at 1600x1200 [v4l2src_calls.c(1289): gst_v4l2src_set_capture (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src6:
Call to S_FMT failed for YU12 @ 1600x1200: Device or resource busy]
libv4l2: error setting pixformat: Device or resource busy
libv4l2: error requesting 4 buffers: Device or resource busy
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Device '/dev/video0' cannot capture at 1600x1200 [v4l2src_calls.c(1289): gst_v4l2src_set_capture (): /GstPipeline:pipeline3/GstV4l2Src:v4l2src8:
Call to S_FMT failed for YU12 @ 1600x1200: Device or resource busy]
libv4l2: error setting pixformat: Device or resource busy
libv4l2: error requesting 4 buffers: Device or resource busy
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Device '/dev/video0' cannot capture at 1600x1200 [v4l2src_calls.c(1289): gst_v4l2src_set_capture (): /GstPipeline:pipeline4/GstV4l2Src:v4l2src9:
Call to S_FMT failed for YU12 @ 1600x1200: Device or resource busy]


---

### Post by BicyclerBoy on 2011-01-18
...

---

### Post by BicyclerBoy on 2011-01-18
Believe it or not Ubuntu has excellent documentation & help on it's website.
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

Your webcam has to be supported by one of these 3 projects.
video4linux  (LinuxTV.org)
Linux UVC   (really good website & listings)
GSPCA

  all (3) have h/w compatibility lists.
I suggest you use your browser to find out.
This support has to be compiled in your kernel version.
It is possible (but not easy) to add later modules to kernel.

To determine the real name of this webcam
plug it in..run from terminal
lsusb
& post the last 10 lines from 
dmesg

---

### Post by Jammanuser on 2011-01-18
> **BicyclerBoy said:**
> Believe it or not Ubuntu has excellent documentation & help on it's website.
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

Your webcam has to be supported by one of these 2 projects.
video4linux  (LinuxTV.org)
GSPCA

both have h/w compatibility lists.
I suggest you use your browser to find out.
This support has to be compiled in your kernel version.
It is possible (but not easy) to add later modules to kernel.

To determine the real name of this webcam
plug it in..run from terminal
lsusb
& post the last 10 lines from 
dmesg

Thanks.
lsusb output:

> 
Bus 007 Device 005: ID 18ec:3299  
Bus 007 Device 003: ID 05ca:18a0 Ricoh Co., Ltd 
Bus 007 Device 002: ID 152e:2507 LG (HLDS) 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 08ff:2810 AuthenTec, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 413c:8156 Dell Computer Corp. 
Bus 001 Device 006: ID 413c:8158 Dell Computer Corp. 
Bus 001 Device 005: ID 413c:8157 Dell Computer Corp. 
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Last 10 lines of dmesg:
> 
[  842.514130] input: USB2.0 PC CAMERA as /devices/pci0000:00/0000:00:1d.7/usb7/7-3/7-3:1.0/input/input14
[  842.718458] usbcore: registered new interface driver snd-usb-audio
[ 1556.437896] usb 7-3: USB disconnect, address 4
[ 2897.300252] usb 7-3: new high speed USB device using ehci_hcd and address 5
[ 2897.437121] usb 7-3: configuration #1 chosen from 1 choice
[ 2897.438263] uvcvideo: Found UVC 1.00 device USB2.0 PC CAMERA (18ec:3299)
[ 2897.440069] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : 0 (exp. 26).
[ 2897.442362] input: USB2.0 PC CAMERA as /devices/pci0000:00/0000:00:1d.7/usb7/7-3/7-3:1.0/input/input15


---

### Post by BicyclerBoy on 2011-01-18
05ca:18a0 Ricoh Co., Ltd   looks like your internal webcam

dmesg only showing driver loading for internal.

Can you unplug the ext webcam & re-run 
lsusb

& then post the difference to previous result ??

---

### Post by Jammanuser on 2011-01-18
> **BicyclerBoy said:**
> 05ca:18a0 Ricoh Co., Ltd   looks like your internal webcam

dmesg only showing driver loading for internal.

[B]Can you unplug the ext webcam & re-run 
lsusb

& then post the difference to previous result ??[/B]

Sure.
> 
Bus 007 Device 003: ID 05ca:18a0 Ricoh Co., Ltd 
Bus 007 Device 002: ID 152e:2507 LG (HLDS) 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 08ff:2810 AuthenTec, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 413c:8156 Dell Computer Corp. 
Bus 001 Device 006: ID 413c:8158 Dell Computer Corp. 
Bus 001 Device 005: ID 413c:8157 Dell Computer Corp. 
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


---

### Post by Jammanuser on 2011-01-18
EDIT: Sorry, double-post.

---

### Post by BicyclerBoy on 2011-01-18
Does not matter this is the other webcam
(as long as there is not three of them)

18ec:3299       USB 2.0 PC Camera (model number QC3231)       ArkMicro

This supported by Linux UVC now.

People were still having problems with it in March 2010.

Would imagine that upgrade to 10.04 might get it working "out of the box".
It is easy enough to upgrade the kernel in 10.04.

If you have to have support in 8.04 you will have to build a kernel module.

Try
lsusb -v -d 18ec:3299

---

### Post by Jammanuser on 2011-01-18
> **BicyclerBoy said:**
> Does not matter this is the other webcam
(as long as there is not three of them)

18ec:3299       USB 2.0 PC Camera (model number QC3231)       ArkMicro

This supported by Linux UVC now.

People were still having problems with it in March 2010.

Would imagine that upgrade to 10.04 might get it working "out of the box".
It is easy enough to upgrade the kernel in 10.04.

If you have to have support in 8.04 you will have to build a kernel module.

[B]Try
lsusb -v -d 18ec:3299[/B]
This after reconnecting the ext webcam, right?

EDIT: I answered my own question: yes, of course.

Here is the output of that command:

> 
Bus 007 Device 006: ID 18ec:3299  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x18ec 
  idProduct          0x3299 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          498
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              320mA
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         0
      bInterfaceCount         2
      bFunctionClass         14 Video
      bFunctionSubClass       3 Video Interface Collection
      bFunctionProtocol       0 
      iFunction               0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      1 Video Control
      bInterfaceProtocol      0 
      iInterface              0 
      VideoControl Interface Descriptor:
        bLength                13
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdUVC               1.00
        wTotalLength           51
        dwClockFrequency       24.000000MHz
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
        bmControls           0x0000200a
          Auto-Exposure Mode
          Exposure Time (Absolute)
          Roll (Absolute)
      VideoControl Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      5 (PROCESSING_UNIT)
      Warning: Descriptor too short
        bUnitID                 2
        bSourceID               1
        wMaxMultiplier          0
        bControlSize            2
        bmControls     0x0000073f
          Brightness
          Contrast
          Hue
          Saturation
          Sharpness
          Gamma
          Backlight Compensation
          Gain
          Power Line Frequency
        iProcessing             0 
        bmVideoStandards     0x 9
          None
          SECAM - 625/50
      VideoControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             3
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID               2
        iTerminal               0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval              10
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
        wTotalLength                      275
        bEndPointAddress                  131
        bmInfo                              0
        bTerminalLink                       3
        bStillCaptureMethod                 2
        bTriggerSupport                     1
        bTriggerUsage                       0
        bControlSize                        1
        bmaControls( 0)                    27
      VideoStreaming Interface Descriptor:
        bLength                            27
        bDescriptorType                    36
        bDescriptorSubtype                  4 (FORMAT_UNCOMPRESSED)
        bFormatIndex                        1
        bNumFrameDescriptors                5
        guidFormat                            {59555932-0000-1000-8000-00aa00389b71}
        bBitsPerPixel                      16
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
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         1
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            640
        wHeight                           480
        dwMinBitRate                   614400
        dwMaxBitRate                 18432000
        dwMaxVideoFrameBufferSize      614400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  4
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
        dwFrameInterval( 2)           1000000
        dwFrameInterval( 3)           2000000
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         2
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            352
        wHeight                           288
        dwMinBitRate                   202752
        dwMaxBitRate                  6082560
        dwMaxVideoFrameBufferSize      202752
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  4
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
        dwFrameInterval( 2)           1000000
        dwFrameInterval( 3)           2000000
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         3
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            320
        wHeight                           240
        dwMinBitRate                   153600
        dwMaxBitRate                  4608000
        dwMaxVideoFrameBufferSize      153600
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  4
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
        dwFrameInterval( 2)           1000000
        dwFrameInterval( 3)           2000000
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         4
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            176
        wHeight                           144
        dwMinBitRate                    50688
        dwMaxBitRate                  1520640
        dwMaxVideoFrameBufferSize       50688
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  4
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
        dwFrameInterval( 2)           1000000
        dwFrameInterval( 3)           2000000
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         5
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            160
        wHeight                           120
        dwMinBitRate                    38400
        dwMaxBitRate                  1152000
        dwMaxVideoFrameBufferSize       38400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  4
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
        dwFrameInterval( 2)           1000000
        dwFrameInterval( 3)           2000000
      VideoStreaming Interface Descriptor:
        bLength                            18
        bDescriptorType                    36
        bDescriptorSubtype                  3 (STILL_IMAGE_FRAME)
        bEndpointAddress                    0
        bNumImageSizePatterns               3
        wWidth( 0)                        640
        wHeight( 0)                       480
        wWidth( 1)                        800
        wHeight( 1)                       600
        wWidth( 2)                       1280
        wHeight( 2)                      1024
        bNumCompressionPatterns             3
      VideoStreaming Interface Descriptor:
        bLength                             6
        bDescriptorType                    36
        bDescriptorSubtype                 13 (COLORFORMAT)
        bColorPrimaries                     0 (Unspecified)
        bTransferCharacteristics            0 (Unspecified)
        bMatrixCoefficients                 0 (Unspecified)
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
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x13e8  3x 1000 bytes
        bInterval               1
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         2
      bInterfaceCount         2
      bFunctionClass          1 Audio
      bFunctionSubClass       1 Control Device
      bFunctionProtocol       0 
      iFunction               4 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      1 Control Device
      bInterfaceProtocol      0 
      iInterface              4 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdADC               1.00
        wTotalLength           40
        bInCollection           1
        baInterfaceNr( 0)       3
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Microphone
        bAssocTerminal          0
        bNrChannels             2
        wChannelConfig     0x0003
          Left Front (L)
          Right Front (R)
        iChannelNames           0 
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                10
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                 2
        bSourceID               1
        bControlSize            1
        bmaControls( 0)      0x00
        bmaControls( 1)      0x03
          Mute
          Volume
        bmaControls( 2)      0x03
          Mute
          Volume
        iFeature                0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             3
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID               2
        iTerminal               0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              4 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              4 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           3
        bDelay                  1 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             1
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        48000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0080  1x 128 bytes
        bInterval               4
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x01
            Sampling Frequency
          bLockDelayUnits         0 Undefined
          wLockDelay              0 Undefined
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)


---

### Post by BicyclerBoy on 2011-01-18
Correct.
You don't get top marks tho' because you didn't post the result !

I doubt it will help as your install is far to out of date sorry.

The only program that stands out from 8.04 & 8.10 is Amarok 1.4.
I still use it with 10.04.

---

### Post by BicyclerBoy on 2011-01-18
Correct.
You don't get top marks tho' because you didn't post the result !

I doubt it will help as your install is far to out of date sorry.

The only program that stands out from 8.04 & 8.10 is Amarok 1.4.
I still use it with 10.04.

---

### Post by Jammanuser on 2011-01-18
> **BicyclerBoy said:**
> Correct.
**You don't get top marks tho' because you didn't post the result !**

Actually I did. :popcorn:
See post above, which I edited. I could have had it up sooner, but the page was having problems loading, sorry.
> 
**I doubt it will help as your install is far to out of date sorry.**

The only program that stands out from 8.04 & 8.10 is Amarok 1.4.
I still use it with 10.04.
Yeah, about that...
I would have upgraded a long time ago, but I watched the reports of those who did, and many of them reported problems with their hardware that they didn't have in 8.10, so I figured I would keep mine at 8.10, because at least it was a stable install, and I had got mostly everything to work in it (though not my webcam). So I opted to install 9.10 to its own partition when it first came out, adding it to my existing multiboot of Windows Vista Home Premium SP1, Windows XP Profession SP3, and Ubuntu 8.10, which I had at that time. But since then, I've only gone into 9.10 a few times, and I mostly use 8.10, so I kind of forgot to stay current with my newer install of ubuntu. ;) But, now that you mention it, I am probably going to go into Ubuntu 9.10 soon, and go ahead and upgrade it to the latest version of Ubuntu. I'll let you know how that goes. Maybe everything, including both my webcams, will work then.

Cheers.

-Jam Man

:guitar:

---

