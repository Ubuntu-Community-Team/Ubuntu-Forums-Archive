---
title: "web-camera"
date: 2009-04-14
forum: Multimedia Software
---

### Post by jedaika on 2009-04-14
Hi everybody! Before all, thanks to all developers!

I have problem with web-camera Microsoft VX-1000 on SN9C105 chip.
When I run any program to capture stream I have only 5 fps at any resolution on ubuntu9.04 at work. At home on ubuntu7.10 - I have 15 fps on 320x240 but it is not ok, because on windows I had full 30 fps on 640x480. Anybody have this problem?
I tried other cameras and have the same result - very poor picture (like 320x240 strength to 640x480 after many compressions) and low fps 5-15 on 320x240, and low than 5 fps on 640x480.

Could anybody help me?

dmesg
[    7.867883] gspca: main v2.5.0 registered
[    7.869575] gspca: probing 045e:00f7
[    7.874568] sonixj: Sonix chip id: 11
[    7.877709] gspca: probe ok
[    7.877724] gspca: probing 045e:00f7
[    7.877735] gspca: probing 045e:00f7
[    7.877764] usbcore: registered new interface driver sonixj
[    7.877807] sonixj: registered


uname -a
Linux jeday-desktop 2.6.28-11-generic #41-Ubuntu SMP Wed Apr 8 04:38:53 UTC 2009 i686 GNU/Linux

ant deviceInfo -Dtest.device=/dev/video0

deviceInfo:
     [java] [ libv4l.c:67 ] Using libv4l version 0.8-libv4l_r97
     [java] name: USB camera
     [java] Device file: /dev/video0
     [java] Supported formats:
     [java] 	JPEG - 8
     [java] Some formats can be JPEG-encoded? Yes
     [java] List of Formats that can be JPEG-encoded:
     [java] 	JPEG - 8
     [java] Some formats can be RGB-converted? Yes
     [java] List of Formats that can be converted to RGB:
     [java] 	JPEG - 8
     [java] Inputs:
     [java] 	Name: sonixj
     [java] 	Type: 2(Camera)
     [java] 	Index: 0
     [java] 	Supported standards:
     [java] 		0(None/Webcam)
     [java] Control: Infrared - min: 0 - max: 1 - step: 1 - value: 0
     [java] Control: Blue Balance - min: 24 - max: 40 - step: 1 - value: 32
     [java] Control: Brightness - min: 0 - max: 65535 - step: 1 - value: 32768
     [java] Control: Red Balance - min: 24 - max: 40 - step: 1 - value: 32
     [java] Control: Contrast - min: 0 - max: 127 - step: 1 - value: 63
     [java] Control: Color - min: 0 - max: 40 - step: 1 - value: 32

---

