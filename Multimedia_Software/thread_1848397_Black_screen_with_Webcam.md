---
title: "Black screen with Webcam"
date: 2011-09-22
forum: Multimedia Software
---

### Post by Soranne on 2011-09-22
Hi everyone,
I have made many google search but non of them helped me.
Here is my problem : I've got one internal webcam and an external. I'd like to use the external for one of my robot, I launch cheese, but for the external webcam I've got a black/grey image...

Here are some commands I launched in Terminal : :
```
lsmod | grep gspca
gspca_zc3xx            45189  0 
gspca_main             21199  1 gspca_zc3xx
videodev               34361  2 gspca_main,uvcvideo
```and
```
lsusb
Bus 004 Device 002: ID eb1a:2761 eMPIA Technology, Inc. EeePC 701 integrated Webcam
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0951:1606 Kingston Technology 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0ac8:301b Z-Star Microelectronics Corp. ZC0301 Webcam
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```with xawtv :
```
.........@eeepc:~/gspcav1-20071224$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.32-32-generic-pae)
xinerama 0: 800x480+0+0
WARNING: No DGA direct video mode for this display.
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_G_STD(std=0x1 [PAL_B]): Argument invalide
ioctl: VIDIOC_S_CTRL(id=9963778;value=18): Erreur d'entrée/sortie
ioctl: VIDIOC_S_STD(std=0x0 []): Argument invalide
libv4l2: error converting / decoding frame data: v4l-convert: error parsing JPEG header: Not a JPG file ?


ioctl: VIDIOC_DQBUF(index=1;type=VIDEO_CAPTURE;bytesused=10990;flags=0x1 [MAPPED];field=NONE;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecode.minutes=0;timecode.hours=0;timecode.userbits="";sequence=271;memory=MMAP): Erreur d'entrée/sortie
libv4l2: error converting / decoding frame data: v4l-convert: error unexpected width / height in JPEG headerexpected: 352x288, header: 320x240

ioctl: VIDIOC_DQBUF(index=0;type=VIDEO_CAPTURE;bytesused=8077;flags=0x1 [MAPPED];field=NONE;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecode.minutes=0;timecode.hours=0;timecode.userbits="";sequence=0;memory=MMAP): Erreur d'entrée/sortie
```Just after having plugged the webcam :
```
sudo tail -n 0 -f /var/log/syslog
Sep 22 17:47:15 eeepc kernel: [  574.832100] usb 1-2: new full speed USB device using uhci_hcd and address 3
Sep 22 17:47:15 eeepc kernel: [  575.030436] usb 1-2: configuration #1 chosen from 1 choice
Sep 22 17:47:15 eeepc kernel: [  575.032417] gspca-2.13.6: probing 0ac8:301b
Sep 22 17:47:16 eeepc kernel: [  576.112281] zc3xx-2.13.6: probe 2wr ov vga 0x0000
Sep 22 17:47:16 eeepc kernel: [  576.211125] zc3xx-2.13.6: probe 3wr vga 1 0x8000
Sep 22 17:47:17 eeepc kernel: [  576.388120] zc3xx-2.13.6: probe 3wr vga 2 0x0000
Sep 22 17:47:17 eeepc kernel: [  576.424123] zc3xx: Unknown sensor - set to TAS5130C
Sep 22 17:47:17 eeepc kernel: [  576.427344] input: zc3xx as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/input/input12
Sep 22 17:47:17 eeepc kernel: [  576.427629] gspca-2.13.6: video1 created
```At first I thought I thought it was a driver conflict so I did things like :


```
sudo modprobe -r gspca_pac7311
```and

```
sudo modprobe -r zc0301 
sudo modprobe gspca_pac7311 
```But none of them worked... :sad:
sudo modprobe gspca_pac7311
Any idea?
Thanks in advance,
 Soranne

---

### Post by perspectoff on 2011-09-22
I can only get one webcam program and one webcam to work at a time. 

I don't think I've ever gotten an external webcam to work on my laptop (that has an internal webcam already).

I use XAWTV, Cheese, Kamoso, and previously Camorama.

---

### Post by Soranne on 2011-09-22
So you mean I need to desactivate the internal webcam?

How to do this?

---

