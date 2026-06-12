---
title: "Webcam with ffmpeg or streamer"
date: 2008-07-04
forum: Multimedia Software
---

### Post by RichardA on 2008-07-04
I have a USB webcam attached to a Linksys NSLU2 (running Debian, as there isn't a Ubuntu build for Arm).

The webcam is seen and a driver loaded:
> 
Linux video capture interface: v2.00
sn9c102: V4L2 driver for SN9C10x PC Camera Controllers v1:1.27
usb 2-1: SN9C10[12] PC Camera Controller detected (vid/pid 0x0C45/0x6009)
usb 2-1: PAS106B image sensor detected
swapped image found
Image loaded to NPE-B Func:0, Rel: 2:1, Status: 82c00000
usb 2-1: Initialization succeeded
usb 2-1: V4L2 device registered as /dev/video0
usbcore: registered new driver sn9c102

But if I try to grab an image or movie from it:
> 
LKGAAE07A:~# ffmpeg -s 320x240 -f video4linux -i /dev/video0 test.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Mar 26 2007 19:25:46, gcc: 4.1.2 20061115 (prerelease) (Debian 4.1.1-21)
/dev/video: No such file or directory
/dev/video0: I/O error occured
Usually that means that input file is truncated and/or corrupted.

> 
LKGAAE07A:~# streamer -d -o test.jpeg
checking writer files [multiple image files] ...
  video name=ppm ext=ppm: ext mismatch [need jpeg]
  video name=pgm ext=pgm: ext mismatch [need jpeg]
  video name=jpeg ext=jpeg: OK
files / video: JPEG (JFIF) / audio: none
vid-open: trying: v4l2-old... 
vid-open: failed: v4l2-old
vid-open: trying: v4l2... 
v4l2: open
v4l2: device info:
  sn9c102 1.0.27 / SN9C10x PC Camera @ usb-0000:00:01.1-1
vid-open: ok: v4l2
movie_init_writer start
setformat: JPEG (JFIF) (320x240): failed
setformat: 12 bit YUV 4:2:0 (planar) (320x240): failed
setformat: 16 bit YUV 4:2:2 (planar) (320x240): failed
setformat: 24 bit TrueColor (BE: rgb) (320x240): failed
setformat: 24 bit TrueColor (LE: bgr) (320x240): failed
no way to get: 320x240 JPEG (JFIF)
movie writer initialisation failed
v4l2: close


Should I be using the ov511 module, instead of sn9c102? Wrong parameters to streamer or ffmpeg? webcam not supported, although it says it is?

---

### Post by danielgroves on 2010-05-21
Did you get anywhere with this?  I am getting the same error in Ubuntu running ffmpeg.  I am using a logitech webcam.

---

### Post by no2498 on 2010-05-21
do your cams work in cheese webcam booth

---

### Post by danielgroves on 2010-05-21
Sorry, should have said.  I worked it out, command needs to be run with super user privileges.

---

### Post by no2498 on 2010-05-21
i do not know how to fix that but you can fix it with out using su mode
i have see it a few times

good luck

---

