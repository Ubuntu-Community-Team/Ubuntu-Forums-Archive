---
title: "wxcam can't open /dev/dsp"
date: 2010-08-24
forum: Multimedia Software
---

### Post by afrodeity on 2010-08-24
This is a continuation of this thread [http://ubuntuforums.org/showthread.php?t=313755](http://ubuntuforums.org/showthread.php?t=313755)

I've tried installing alsa-oss and alsa-compat but problem still not solved.

Thinking now I either have to edit the asound.conf file or find something similar to the festival soundrc fix.

Any ideas?

---

### Post by ArunavAm on 2010-12-03
same problem here.. I am using wxcam (webcam app) and while recording video, it shows this... plz help..

---

### Post by Yellow Pasque on 2010-12-03
If you're using pulseaudio, use padsp to start wxcam. Otherwise, either find a way to set wxcam not to use OSS sound or roll your own kernel with OSS enabled, because Ubuntu disabled OSS in their maverick kernel.

---

### Post by afrodeity on 2010-12-04
forgot about this thread, I solved the problem but good to be reminded about this issue, disabling oss is shortsighted IMHO.

[http://u8untu.blogetery.com/2010/08/26/getting-wxcam-working-with-lucid/](http://u8untu.blogetery.com/2010/08/26/getting-wxcam-working-with-lucid/)

---

### Post by sijar on 2011-02-06
[@Temüjin]("http://ohioloco.ubuntuforums.org/member.php?u=327594")
So I try to run wxcam through pulseaudio using the following command
[B]$ padsp -d wxcam
[/B]although the wxcam started ok,
My wxcam is been set to use xdiv format to enable sound during recording
but while recording the I stll the same error
[B]"Cannot open /dev/dsp.
Video file will be recorded without audio track"

[/B]Please help me in fixing this issue[B]
-------------------------------------------------------------------------------
$ padsp -d wxcam[/B]
Determining video4linux API version...
Using video4linux 2 API
VIDIOC_ENUM_FRAMESIZES: Invalid argument
V4L2_CID_GAMMA is not supported
Determining pixel format...
pixel format: YUV 4:2:2 (YUYV)
Found V4L2_PIX_FMT_YUYV pixel format
pixel format: MJPEG
Found V4L2_PIX_FMT_MJPEG pixel format
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd2
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 3 extraneous bytes before marker 0xd2
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 4 extraneous bytes before marker 0xd2
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd0
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd3
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd1
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd3
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd3
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd2
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd5
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd3
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 3 extraneous bytes before marker 0xd5
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 3 extraneous bytes before marker 0xd6
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd3
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd7
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd7
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd2
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 3 extraneous bytes before marker 0xd7
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd7
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd4
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 3 extraneous bytes before marker 0xd5
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd7
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd2
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 5 extraneous bytes before marker 0xd6
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 3 extraneous bytes before marker 0xd4
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd4
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd0
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd0
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 3 extraneous bytes before marker 0xd5
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd3
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 3 extraneous bytes before marker 0xd0
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 4 extraneous bytes before marker 0xd1
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 3 extraneous bytes before marker 0xd5
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd5
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd5
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd0
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd0
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd0
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 4 extraneous bytes before marker 0xd6
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd2
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd1
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd1
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd4
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd4
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd0
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 4 extraneous bytes before marker 0xd3
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd4
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd2
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 3 extraneous bytes before marker 0xd2
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd0
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd4
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd6
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd5
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd6
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd6
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd2
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd1
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd3
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd6
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 8 extraneous bytes before marker 0xd7
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd0
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd6
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd2
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd3
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd1
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd4
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd0
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd6
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd5
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd4
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd0
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd6
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd4
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd3
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd1
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd7
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd2
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd1
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd3
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd4
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
[B]Corrupt JPEG data: 1 extraneous bytes before marker 0xd3
open of  failed: No such file or directory
[/B]--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd4
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd1
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd7
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd3
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd5
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd1
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd2
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 4 extraneous bytes before marker 0xd1
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd0
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 3 extraneous bytes before marker 0xd2
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd5
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd2
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd3
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd7
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd4
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd1
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd4
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd2
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd0
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 5 extraneous bytes before marker 0xd0
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd1
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 3 extraneous bytes before marker 0xd0
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd3
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd4
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd6
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd4
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd6
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd5
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 4 extraneous bytes before marker 0xd0
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 3 extraneous bytes before marker 0xd7
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd3
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd6
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd6
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd6
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd0
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd4
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd2
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd1
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd0
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd7
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd0
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd3
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd2
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd7
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd6
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 3 extraneous bytes before marker 0xd3
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 4 extraneous bytes before marker 0xd7
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd3
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd7
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd6
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd0
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd1
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd1
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd4
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd7
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
[B]Corrupt JPEG data: 1 extraneous bytes before marker 0xd7
/home/sijar/Videos/Webcam/video.avi written: 640x480, 1334396 bytes
[/B]--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd3
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 4 extraneous bytes before marker 0xd3
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd7
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd6
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd2
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd1
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd3
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd5
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 1 extraneous bytes before marker 0xd5
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 6 extraneous bytes before marker 0xd2
--DEBUG: [wxcam] Generating standard Huffman tables for this frame.
Corrupt JPEG data: 2 extraneous bytes before marker 0xd2

---

