---
title: "zoneminder status is '255'"
date: 2016-02-27
forum: Multimedia Software
---

### Post by zrock2 on 2016-02-27
reinstalled Pc  
[COLOR=#000000][FONT=arial]Ubuntu 14.04.4 LTS
[/FONT][/COLOR]I came again zoneminder
I installed v 1.29.0


monitor [COLOR=#000000][FONT=Times New Roman]Unable to probe local cameras, status is '255'

[/FONT][/COLOR]yanko@nybet:/dev$ sudo zmu -d /dev/video0 -q -v -U admin -P *****
Video Device: /dev/video0
General Capabilities
  Driver: bttv
  Card: BT878 video (GrandTec Multi Cap
  Bus: PCI:0000:05:0a.0
  Version: 4.2.8
  Type: 0x85200015
    Supports video capture (X)
    Does not support video output
    Supports frame buffer overlay
    Supports VBI capture
    Does not support VBI output
    Does not support sliced VBI capture
    Does not support sliced VBI output
    Does not support video output overlay
    Does not have tuner
    Does not have audio in and/or out
    Does not have radio
    Supports read/write i/o (X)
    Does not support async i/o
    Supports streaming i/o (X)
    Standards:
      NTSC
      NTSC-M
      NTSC-M-JP
      NTSC-M-KR
      PAL
      PAL-BG
      PAL-H
      PAL-I
      PAL-DK
      PAL-M
      PAL-N
      PAL-Nc
      PAL-60
      SECAM
      SECAM-B
      SECAM-G
      SECAM-H
      SECAM-DK
      SECAM-L
      SECAM-Lc
  Formats:
    8-bit Greyscale (GREY)
    8-bit Dithered RGB (BTTV) (HI24)
    16-bit A/XRGB 1-5-5-5 (RGBO)
    16-bit A/XRGB 1-5-5-5 BE (RGBQ)
    16-bit RGB 5-6-5 (RGBP)
    16-bit RGB 5-6-5 BE (RGBR)
    24-bit BGR 8-8-8 (BGR3)
    32-bit BGRA/X 8-8-8-8 (BGR4)
    32-bit A/XRGB 8-8-8-8 (RGB4)
    YUYV 4:2:2 (YUYV)
    UYVY 4:2:2 (UYVY)
    Planar YVU 4:2:2 (422P)
    Planar YUV 4:2:0 (YU12)
    Planar YVU 4:2:0 (YV12)
    Planar YUV 4:1:1 (411P)
    Planar YUV 4:1:0 (YUV9)
    Planar YVU 4:1:0 (YVU9)
Crop Capabilities
  Bounds: 1063 x 608
  Default: 924 x 576
  Current: 924 x 576
Inputs: 4
  Input 0
    Name: Composite0
    Type: Camera
    Audioset: 00000000
    Standards: 0xffbfff
    Power on  (X)
    Signal detected  (X)
    Colour Signal detected
    Horizontal Lock detected
  Input 1
    Name: Composite1
    Type: Camera
    Audioset: 00000000
    Standards: 0xffbfff
    Power on  (X)
    Signal detected  (X)
    Colour Signal detected
    Horizontal Lock detected
  Input 2
    Name: Composite2
    Type: Camera
    Audioset: 00000000
    Standards: 0xffbfff
    Power on  (X)
    Signal detected  (X)
    Colour Signal detected
    Horizontal Lock detected
  Input 3
    Name: Composite3
    Type: Camera
    Audioset: 00000000
    Standards: 0xffbfff
    Power on  (X)
    Signal detected  (X)
    Colour Signal detected
    Horizontal Lock detected

yanko@nybet:/dev$ dmesg | grep video
[   15.643994] Linux video capture interface: v2.00
[   16.706556] bttv: 0: registered device video0
yanko@nybet:/dev$

yanko@nybet:/dev$ dmesg | grep bttv
[   16.572216] bttv: driver version 0.9.19 loaded
[   16.572224] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   16.572940] bttv: Bt8xx card found (0)
[   16.573212] bttv: 0: Bt878 (rev 17) at 0000:05:0a.0, irq: 21, latency: 66, mmio: 0xf0500000
[   16.573234] bttv: 0: using: GrandTec Multi Capture Card (Bt878) [card=77,insmod option]
[   16.573716] bttv: 0: tuner absent
[   16.573757] bttv: 0: Setting PLL: 28636363 => 35468950 (needs up to 100ms)
[   16.705997] bttv: PLL set ok
[   16.706556] bttv: 0: registered device video0
[   16.706785] bttv: 0: registered device vbi0
yanko@nybet:/dev$

monitor glows green  but no picture
on  Zones	I see the camera

where is the problem

---

### Post by yancek on 2016-02-27
You have a number of "does not support..." messages in the output you posted.  If you can see the main page of zoneminder, the first thing I would check is the Log tab in the upper right.

---

