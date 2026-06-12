---
title: "How to record audio and video from a webcam?"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by kung fu buntu on 2007-10-06
I would like to know how can I record audio and video simultaneously from my Logitech QuickCam Fusion, while the application displays what is being recorded.
*exhales*
I've spent too many hours on this and still don't have things working.
I've tried a lot of programs but they're not working for me.

I have my webcam working with aMSN just fine, I have support for both audio and video... so this means there is driver support.
I can also record video using luvcview, but it doesn't support audio.


**xawtv**
Doesn't work!```
xawtv -v -c /dev/video1 -C /dev/dsp2 -nodga

/usr/bin/xawtv: line 10: [: (opcode:: binary operator expected
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.21-2-amd64)
Warning: Cannot convert string "-c" to type Int
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
v4l-conf had some trouble, trying to continue anyway
v4l2: WARNING: framebuffer size mismatch
v4l2: me=1280x1024 v4l=0x0
station "/dev/video1" not found
```

**ffmpeg**
Can't get audio and doesn't display what is being captured.
```
ffmpeg -v 100 -f oss -i /dev/dsp2  -f video4linux2 -s 320x240 -i /dev/video1  -f m4v test.m4v
```

**mencoder**
Doesn't work
```
mencoder -v -tv device=/dev/video1:driver=v4l2:outfmt=yuy2:adevice=/dev/dsp2:forceaudio -vc rawyuy2 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=320 -oac mp3lame -lameopts cbr:br=128:mode=0 -o 3.avi tv://

MEncoder dev-SVN-rUNKNOWN-4.2.1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Configuration: --prefix=/usr --confdir=/etc/mplayer --datadir=/usr/share/mplayer --enable-xmga --enable-mga --enable-joystick --enable-faad-external --disable-tremor-internal --enable-libamr_nb --enable-libamr_wb --language=all --enable-largefiles --enable-menu --with-extraincdir=/usr/include/ffmpeg -I./libavformat -I./libswscale -I./libavutil -I./libpostproc -I./libavcodec --enable-radio --disable-libdvdcss-internal --enable-lirc --enable-radio-capture --enable-png --enable-xvmc --with-xvmclib=XvMCW --enable-fbdev --enable-directfb --enable-tdfxfb --enable-s3fb
init_freetype
get_path('font/font.desc') -> '/home/kaizoku/.mplayer/font/font.desc'
font: can't open file: /home/kaizoku/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
STREAM: [tv] tv://
STREAM: Description: TV Input
STREAM: Author: Benjamin Zores, Albeu
STREAM: Comment:
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: ioctl get standard failed: Invalid argument
Selected device: UVC Camera (046d:08ca)
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Format MJPEG  ( 0 bits, MJPEG): Unknown 0x47504a4d
 Format YUYV   (16 bits, YUV 4:2:2 (YUYV)): Packed YUY2
 Current format: YUYV
v4l2: set format: YUYV
v4l2: set input: 0
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
Selected norm : pal
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
==> Found video stream: 0
v4l2: get format: YUYV
v4l2: get fps: nan
v4l2: get width: 640
v4l2: get height: 480
ioctl dsp getfmt: 0
Supported formats: 1f9
ioctl dsp setfmt: 0
ioctl dsp stereo: 0 (req: 1)
ioctl dsp speed: 0
ioctl dsp trigger: 0
trigger: 1
ioctl dsp trigger: 0
ioctl dsp getblocksize: 0
blocksize: 16384
v4l2: set audio samplerate: 44100
v4l2: get audio format: 9
==> Found audio stream: 0
v4l2: get audio samplerate: 44100
v4l2: get audio samplesize: 2
v4l2: get audio channels: 2
  TV audio: 2 channels, 16 bits, 44100 Hz
Audio capture - buffer 256 blocks of 16384 bytes, skew average from 16 meas.
Floating point exception
```


I've tried changing parameters but.... couldn't solve anything.

Any help is greatly appreciated.

---

### Post by kung fu buntu on 2007-10-12
anyone?

---

### Post by metol on 2007-10-13
I'm having similar headaches with my newly purchased Logitech Quickcam 9000 Pro.  I believe that this webcam as well as yours are not supported under the older Video4Linux (4VL) API since it is now deprecated.  However, it is supported under the newer Video4Linux2 (4VL2) API and UVC.  As a result, I found that many older apps (like Camorama) will not work.  I have found a very nice utility named 'videoview' that works quite well for video capture and frame grabbing... give it a try.  Here are the apps I have gotten to work thus far:

- Ekiga
- videoview
- luvciew (you first need to install libsdl1.2-dev)
- fswebcam (fswebcam -l 5 -r 640x480 test.jpg  <<< here is a command line example captures a frame every 5 seconds and stores it in a jpeg)

Now with all of these apps, I have been _unable to get the sound to work_ at all.  I finally gave up and bought a cheap microphone to use via ALSA until I get that one sorted out.  If you have any luck with sound, please let me know.

Here are some useful links:
[Linux 4VL Wiki]("http://www.linuxtv.org/v4lwiki/index.php/Webcams")
[Linux UVC Info]("http://openfacts.berlios.de/index-en.phtml?title=Linux_UVC")

---

### Post by kosson on 2007-11-23
I bought a quickcam 9000 in order to produce some nice videotuts. The big surprise was when I saw only Ekiga knows about my camera and that's all folks...

Hmmm
 Condemned to use windows... It'a pain... make some captures in win go back to linbox assemble in cinelerra... 

Why ](*,)

---

