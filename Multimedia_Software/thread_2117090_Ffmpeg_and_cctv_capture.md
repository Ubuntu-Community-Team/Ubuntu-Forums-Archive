---
title: "Ffmpeg and cctv capture"
date: 2013-02-17
forum: Multimedia Software
---

### Post by timsdeepsky on 2013-02-17
Hi,,
How can i make ffmpeg capture video from my Brooktree Corporation Bt878 Video Capture card on video 2 input 1 location(has 4 inputs),,from 4pm until 7pm daily??..I have 3 brooktree cards installed and have captured from all 3 using zoneminder....But i want to use ffmpeg for this particular card....For some reason i can not access the card from xawtv,,or with this ffmpeg command ```
ffmpeg -f video4linux2 -s 640x480 -r ntsc -i /dev/video2 -qscale 3 video.mpeg
```....I can capture video from this card with zoneminder and Vlc using video 2,input 1....Am i missing a channel setting in the ffmpeg code??..I have used multiple codes and searched and i am at a loss on this one....Any link or info would be appreciated....
Release 12.04 (precise) 64-bit....
Kernel Linux 3.2.0-37-generic....
GNOME 3.4.2....
Thanks....

---

### Post by FakeOutdoorsman on 2013-02-17
Please provide the complete ffmpeg console output resulting from your ffmpeg command.

---

### Post by timsdeepsky on 2013-02-17
```
tim@tim-quad-core:~$ ffmpeg -f video4linux2 -s 640x480 -r ntsc -i /dev/video2 -qscale 3 video.mpeg
ffmpeg version git-2012-04-29-46eba43 Copyright (c) 2000-2012 the FFmpeg developers
  built on Apr 29 2012 11:57:53 with gcc 4.6.3
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-nonfree --enable-version3 --enable-x11grab
  libavutil      51. 48.100 / 51. 48.100
  libavcodec     54. 17.101 / 54. 17.101
  libavformat    54.  3.100 / 54.  3.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 72.100 /  2. 72.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0. 11.100 /  0. 11.100
  libpostproc    52.  0.100 / 52.  0.100
[video4linux2,v4l2 @ 0x16ad320] ioctl set time per frame(1001/30000) failed
/dev/video2: Input/output error
```
Thank You....

---

### Post by FakeOutdoorsman on 2013-02-17
There has been some recent activity on v4l2.c in FFmpeg, so you may be experiencing a bug that has been fixed recently. See [Updating FFmpeg](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide#update) in the compile guide. You may skip fdk-aac, libvpx, and opus sections since you probably don't have existing source directories for those encoders.

---

### Post by timsdeepsky on 2013-02-17
Thank you FakeOutdoorsman....I will try it and let you know how it goes....

---

### Post by timsdeepsky on 2013-02-17
FakeOutdoorsman,,
I went ahead and completely reinstalled x264 and ffmpeg from this page [http:////ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide#update]("http:////ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide#update")....After this install i was able to make xawtv record video from this card now by using this code ```
xawtv -device /dev/video2
```,,,,but once it launches the screen is blue and i have to change the video source in xawtv to "composite 1",,,,then it shows the video and can record....I know for a fact this card is at "/dev/video2"....Zoneminder is currently using the cards at /dev/video0 and /dev/video1,,,,and i can make zoneminder pick up and record from the card at /dev/video2,,channel 1....But when i use this code ```
ffmpeg -f video4linux2 -s 640x480 -r ntsc -i /dev/video2 -qscale 3 video.mpeg
```,,it will show it recording in terminal,,but the final video is blue screen,,and i get this in terminal ```
tim@tim-quad-core:~$ ffmpeg -f video4linux2 -s 640x480 -r ntsc -i /dev/video2 -qscale 3 video.mpeg
ffmpeg version N-43174-gf4e29c4 Copyright (c) 2000-2013 the FFmpeg developers
  built on Feb 17 2013 17:12:25 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: --enable-gpl --enable-libass --enable-libfaac --enable-libfdk-aac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-librtmp --enable-libtheora --enable-libvorbis --enable-libvpx --enable-x11grab --enable-libx264 --enable-nonfree --enable-version3
  libavutil      52. 17.102 / 52. 17.102
  libavcodec     54. 92.100 / 54. 92.100
  libavformat    54. 63.100 / 54. 63.100
  libavdevice    54.  3.103 / 54.  3.103
  libavfilter     3. 38.103 /  3. 38.103
  libswscale      2.  2.100 /  2.  2.100
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  2.100 / 52.  2.100
[video4linux2,v4l2 @ 0x34951e0] The driver does not allow to change time per frame
[video4linux2,v4l2 @ 0x34951e0] Estimating duration from bitrate, this may be inaccurate
Input #0, video4linux2,v4l2, from '/dev/video2':
  Duration: N/A, start: 1361150597.368103, bitrate: 110481 kb/s
    Stream #0:0: Video: rawvideo (I420 / 0x30323449), yuv420p, 640x480, 110481 kb/s, 29.97 fps, 29.97 tbr, 1000k tbn, 1000k tbc
Please use -q:a or -q:v, -qscale is ambiguous
[mpeg @ 0x34960e0] VBV buffer size not set, muxing may fail
Output #0, mpeg, to 'video.mpeg':
  Metadata:
    encoder         : Lavf54.63.100
    Stream #0:0: Video: mpeg1video, yuv420p, 640x480, q=2-31, 200 kb/s, 90k tbn, 29.97 tbc
Stream mapping:
  Stream #0:0 -> #0:0 (rawvideo -> mpeg1video)
Press [q] to stop, [?] for help
frame=   26 fps=0.0 q=3.0 size=      14kB time=00:00:00.80 bitrate= 143.2kbits/sframe=   41 fps= 41 q=3.0 size=      20kB time=00:00:01.30 bitrate= 125.9kbits/sframe=   56 fps= 37 q=3.0 size=      26kB time=00:00:01.80 bitrate= 118.2kbits/sframe=   71 fps= 35 q=3.0 size=      32kB time=00:00:02.30 bitrate= 113.9kbits/s
```,,,,and it continues to record in terminal until i kill it....Odd....Thanks for your help....

---

### Post by timsdeepsky on 2013-02-17
Could i be missing part of the ffmpeg code that specifies the port of my card??..My exact card is a "Bluecherry-PV-143 - 4 port video capture card"....Thanks....

---

### Post by timsdeepsky on 2013-02-17
Using this gstreamer code....
```
gst-launch v4l2src device=/dev/video2 ! queue ! ffenc_mpeg2video bitrate=2000000 ! mpegtsmux ! filesink location=bt878.mpg
```
i get blue screen also....

---

### Post by FakeOutdoorsman on 2013-02-17
What are the outputs of:
```
v4l2-ctl --list-formats-ext
```
and:
```
ffmpeg -f video4linux2 -list_formats all -i /dev/video2
```
and:
```
ffmpeg -f video4linux2 -list_standards all -i /dev/video2
```

---

### Post by timsdeepsky on 2013-02-18
Out put of "v4l2-ctl --list-formats-ext"
```
tim@tim-quad-core:~$ v4l2-ctl --list-formats-ext
ioctl: VIDIOC_ENUM_FMT
	Index       : 0
	Type        : Video Capture
	Pixel Format: 'GREY'
	Name        : 8 bpp, gray

	Index       : 1
	Type        : Video Capture
	Pixel Format: 'HI24'
	Name        : 8 bpp, dithered color

	Index       : 2
	Type        : Video Capture
	Pixel Format: 'RGBO'
	Name        : 15 bpp RGB, le

	Index       : 3
	Type        : Video Capture
	Pixel Format: 'RGBQ'
	Name        : 15 bpp RGB, be

	Index       : 4
	Type        : Video Capture
	Pixel Format: 'RGBP'
	Name        : 16 bpp RGB, le

	Index       : 5
	Type        : Video Capture
	Pixel Format: 'RGBR'
	Name        : 16 bpp RGB, be

	Index       : 6
	Type        : Video Capture
	Pixel Format: 'BGR3'
	Name        : 24 bpp RGB, le

	Index       : 7
	Type        : Video Capture
	Pixel Format: 'BGR4'
	Name        : 32 bpp RGB, le

	Index       : 8
	Type        : Video Capture
	Pixel Format: 'RGB4'
	Name        : 32 bpp RGB, be

	Index       : 9
	Type        : Video Capture
	Pixel Format: 'YUYV'
	Name        : 4:2:2, packed, YUYV

	Index       : 10
	Type        : Video Capture
	Pixel Format: 'YUYV'
	Name        : 4:2:2, packed, YUYV

	Index       : 11
	Type        : Video Capture
	Pixel Format: 'UYVY'
	Name        : 4:2:2, packed, UYVY

	Index       : 12
	Type        : Video Capture
	Pixel Format: '422P'
	Name        : 4:2:2, planar, Y-Cb-Cr

	Index       : 13
	Type        : Video Capture
	Pixel Format: 'YU12'
	Name        : 4:2:0, planar, Y-Cb-Cr

	Index       : 14
	Type        : Video Capture
	Pixel Format: 'YV12'
	Name        : 4:2:0, planar, Y-Cr-Cb

	Index       : 15
	Type        : Video Capture
	Pixel Format: '411P'
	Name        : 4:1:1, planar, Y-Cb-Cr

	Index       : 16
	Type        : Video Capture
	Pixel Format: 'YUV9'
	Name        : 4:1:0, planar, Y-Cb-Cr

	Index       : 17
	Type        : Video Capture
	Pixel Format: 'YVU9'
	Name        : 4:1:0, planar, Y-Cr-Cb

tim@tim-quad-core:~$ 

```

Out put of "ffmpeg -f video4linux2 -list_formats all -i /dev/video2"

```
tim@tim-quad-core:~$ ffmpeg -f video4linux2 -list_formats all -i /dev/video2
ffmpeg version N-43174-gf4e29c4 Copyright (c) 2000-2013 the FFmpeg developers
  built on Feb 17 2013 17:12:25 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: --enable-gpl --enable-libass --enable-libfaac --enable-libfdk-aac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-librtmp --enable-libtheora --enable-libvorbis --enable-libvpx --enable-x11grab --enable-libx264 --enable-nonfree --enable-version3
  libavutil      52. 17.102 / 52. 17.102
  libavcodec     54. 92.100 / 54. 92.100
  libavformat    54. 63.100 / 54. 63.100
  libavdevice    54.  3.103 / 54.  3.103
  libavfilter     3. 38.103 /  3. 38.103
  libswscale      2.  2.100 /  2.  2.100
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  2.100 / 52.  2.100
[video4linux2,v4l2 @ 0x1a246e0] Raw       :      gray :          8 bpp, gray :
[video4linux2,v4l2 @ 0x1a246e0] Raw       : Unsupported : 8 bpp, dithered color :
[video4linux2,v4l2 @ 0x1a246e0] Raw       :  rgb555le :       15 bpp RGB, le :
[video4linux2,v4l2 @ 0x1a246e0] Raw       :  rgb555be :       15 bpp RGB, be :
[video4linux2,v4l2 @ 0x1a246e0] Raw       :  rgb565le :       16 bpp RGB, le :
[video4linux2,v4l2 @ 0x1a246e0] Raw       :  rgb565be :       16 bpp RGB, be :
[video4linux2,v4l2 @ 0x1a246e0] Raw       :     bgr24 :       24 bpp RGB, le :
[video4linux2,v4l2 @ 0x1a246e0] Raw       :      bgr0 :       32 bpp RGB, le :
[video4linux2,v4l2 @ 0x1a246e0] Raw       :      0rgb :       32 bpp RGB, be :
[video4linux2,v4l2 @ 0x1a246e0] Raw       :   yuyv422 :  4:2:2, packed, YUYV :
[video4linux2,v4l2 @ 0x1a246e0] Raw       :   yuyv422 :  4:2:2, packed, YUYV :
[video4linux2,v4l2 @ 0x1a246e0] Raw       :   uyvy422 :  4:2:2, packed, UYVY :
[video4linux2,v4l2 @ 0x1a246e0] Raw       :   yuv422p : 4:2:2, planar, Y-Cb-Cr :
[video4linux2,v4l2 @ 0x1a246e0] Raw       :   yuv420p : 4:2:0, planar, Y-Cb-Cr :
[video4linux2,v4l2 @ 0x1a246e0] Raw       :   yuv420p : 4:2:0, planar, Y-Cr-Cb :
[video4linux2,v4l2 @ 0x1a246e0] Raw       :   yuv411p : 4:1:1, planar, Y-Cb-Cr :
[video4linux2,v4l2 @ 0x1a246e0] Raw       :   yuv410p : 4:1:0, planar, Y-Cb-Cr :
[video4linux2,v4l2 @ 0x1a246e0] Raw       :   yuv410p : 4:1:0, planar, Y-Cr-Cb :
/dev/video2: Immediate exit requested
tim@tim-quad-core:~$ 

```

Out put of "ffmpeg -f video4linux2 -list_standards all -i /dev/video2"
```
tim@tim-quad-core:~$ ffmpeg -f video4linux2 -list_standards all -i /dev/video2
ffmpeg version N-43174-gf4e29c4 Copyright (c) 2000-2013 the FFmpeg developers
  built on Feb 17 2013 17:12:25 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: --enable-gpl --enable-libass --enable-libfaac --enable-libfdk-aac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-librtmp --enable-libtheora --enable-libvorbis --enable-libvpx --enable-x11grab --enable-libx264 --enable-nonfree --enable-version3
  libavutil      52. 17.102 / 52. 17.102
  libavcodec     54. 92.100 / 54. 92.100
  libavformat    54. 63.100 / 54. 63.100
  libavdevice    54.  3.103 / 54.  3.103
  libavfilter     3. 38.103 /  3. 38.103
  libswscale      2.  2.100 /  2.  2.100
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  2.100 / 52.  2.100
[video4linux2,v4l2 @ 0x30366e0]  0,             b000, NTSC
[video4linux2,v4l2 @ 0x30366e0]  1,             1000, NTSC-M
[video4linux2,v4l2 @ 0x30366e0]  2,             2000, NTSC-M-JP
[video4linux2,v4l2 @ 0x30366e0]  3,             8000, NTSC-M-KR
[video4linux2,v4l2 @ 0x30366e0]  4,               ff, PAL
[video4linux2,v4l2 @ 0x30366e0]  5,                7, PAL-BG
[video4linux2,v4l2 @ 0x30366e0]  6,                8, PAL-H
[video4linux2,v4l2 @ 0x30366e0]  7,               10, PAL-I
[video4linux2,v4l2 @ 0x30366e0]  8,               e0, PAL-DK
[video4linux2,v4l2 @ 0x30366e0]  9,              100, PAL-M
[video4linux2,v4l2 @ 0x30366e0] 10,              200, PAL-N
[video4linux2,v4l2 @ 0x30366e0] 11,              400, PAL-Nc
[video4linux2,v4l2 @ 0x30366e0] 12,              800, PAL-60
[video4linux2,v4l2 @ 0x30366e0] 13,           ff0000, SECAM
[video4linux2,v4l2 @ 0x30366e0] 14,            10000, SECAM-B
[video4linux2,v4l2 @ 0x30366e0] 15,            40000, SECAM-G
[video4linux2,v4l2 @ 0x30366e0] 16,            80000, SECAM-H
[video4linux2,v4l2 @ 0x30366e0] 17,           320000, SECAM-DK
[video4linux2,v4l2 @ 0x30366e0] 18,           400000, SECAM-L
[video4linux2,v4l2 @ 0x30366e0] 19,           800000, SECAM-Lc
/dev/video2: Immediate exit requested
tim@tim-quad-core:~$ 

```

Thanks....

---

### Post by timsdeepsky on 2013-02-18
I had success accessing and recording from this card today using mencoder
```
mencoder tv:// -tv driver=v4l2:device=/dev/video2:input=1:width=656:height=492:fps=15:outfmt=mjpeg -nosound -ovc copy -o test.avi
```
....But no luck still with ffmpeg....

---

### Post by FakeOutdoorsman on 2013-02-19
Perhaps usage of the "-channel" and/or "-standard" V4L2 private options will be useful. Other than that I don't have any ideas and don't have access to similar hardware. See "V4L2 indev AVOptions" in "ffmpeg -h full" and [ffmpeg Video4Linux2 docs](http://ffmpeg.org/ffmpeg-devices.html#video4linux2_002c-v4l2).

---

### Post by evilsoup on 2013-02-19
Use

```

ls /dev/v4l/by-id

```

this should give you a list of your connected v4l2 devices. In my case, instead of using /dev/video0 to capture my webcam, I can use

```

ffmpeg -f v4l2 -i /dev/v4l/by-id/usb-Sonix_Technology_Co.__Ltd._USB_2.0_Camera_SN0001-video-index0 [output options] output.file

```

I don't actually know if this will solve your issue, but I hope it helps.

---

### Post by timsdeepsky on 2013-02-19
I just realized that when i use [COLOR="Red"]/dev/video2[/COLOR] with ffmpeg on a 4 port brooktree card it defaults to the "0" port....Like an idiot i had it on port "1"....Seems the ports are numbered 0,1,2,3, on my 4 port card....So i moved my bnc plug to the first port and ffmpeg was able to capture with this ```
ffmpeg -f video4linux2 -s 640x480 -r ntsc -i /dev/video2 -qscale 3 video.mpeg
```....Thanks for all your help FakeOutdoorsman and evilsoup....Now i have to figure out how to get ffmpeg to capture from the card and save it to the hard drive everyday from 5pm to 7pm....Thanks again....I appreciate it greatly....

---

