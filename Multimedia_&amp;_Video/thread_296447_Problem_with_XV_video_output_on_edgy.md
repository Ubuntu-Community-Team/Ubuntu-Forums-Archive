---
title: "Problem with XV video output on edgy"
date: 2006-11-09
forum: Multimedia &amp; Video
---

### Post by jlm on 2006-11-09
Hello,

After the upgrade from Breezy (trough Dapper), the Xv video output doesn't work anymore : When I try to watch a .avi (xvid codec), the video output is black and I only the sound is played.

The X11 output is working but seems worse than the xv one.

I have a Dell laptop with a X300 ati video card, it is plugged on a crt screen. I'm using the fre  driver ATi (not fglrx)

By the way, when I've upgraded to edgy, I some problem becaus the latest driver was not upgraded.

I don't find any relevant error message :

For mplayer I have :

```
mplayer -vo xv "[Indymedia]_(2006-11-05)_1mai-2nov-resume-oaxaca.avi"
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU:         Intel(R) Pentium(R) M processor 1.86GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing [Indymedia]_(2006-11-05)_1mai-2nov-resume-oaxaca.avi.
AVI file format detected.
VIDEO:  [FMP4]  720x576  24bpp  25.000 fps  860.7 kbps (105.1 kbyte/s)
==========================================================================
Requested audio codec family [mp3] (afm=mp3lib) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [ffmp3] afm: ffmpeg (FFmpeg MPEG layer-3 audio decoder)
==========================================================================
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
alsa-init: using device default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12
```


and from xvinfo :

```
Vendor: , Model: 
Num hsync: 1, Num vsync: 1
hsync range 0:  30.00 - 100.00
vsync range 0:  50.00 - 160.00
menut@villon:~/Downloads$ xvinfo 
X-Video Extension version 2.2
screen #0
  Adaptor #0: "ATI Radeon Video Overlay"
    number of ports: 1
    port base: 73
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x23
      depth 24, visualID 0x24
      depth 24, visualID 0x25
      depth 24, visualID 0x26
      depth 24, visualID 0x27
      depth 24, visualID 0x28
      depth 24, visualID 0x29
      depth 24, visualID 0x2a
      depth 24, visualID 0x2b
      depth 24, visualID 0x2c
      depth 24, visualID 0x2d
      depth 24, visualID 0x2e
      depth 24, visualID 0x2f
      depth 24, visualID 0x30
      depth 24, visualID 0x31
      depth 24, visualID 0x32
    number of attributes: 22
      "XV_DEVICE_ID" (range 0 to -1)
              client gettable attribute (current value is 108)
      "XV_LOCATION_ID" (range 0 to -1)
              client gettable attribute (current value is 109)
      "XV_INSTANCE_ID" (range 0 to -1)
              client gettable attribute (current value is 110)
      "XV_DUMP_STATUS" (range 0 to 1)
              client settable attribute
      "XV_SET_DEFAULTS" (range 0 to 1)
              client settable attribute
      "XV_AUTOPAINT_COLORKEY" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_COLORKEY" (range 0 to -1)
              client settable attribute
              client gettable attribute (current value is 66051)
      "XV_DOUBLE_BUFFER" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_OVERLAY_ALPHA" (range 0 to 255)
              client settable attribute
              client gettable attribute (current value is 255)
      "XV_GRAPHICS_ALPHA" (range 0 to 255)
              client settable attribute
              client gettable attribute (current value is 255)
      "XV_ALPHA_MODE" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_BRIGHTNESS" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_CONTRAST" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_SATURATION" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is -10)
      "XV_COLOR" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is -10)
      "XV_HUE" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_RED_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_GREEN_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_BLUE_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_SWITCHCRT" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_GAMMA" (range 100 to 10000)
              client settable attribute
              client gettable attribute (current value is 1000)
      "XV_COLORSPACE" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
    maximum XvImage size: 2048 x 2048
    Number of image formats: 8
      id: 0x41424752 (RGBA)
        guid: 52474241-0000-0010-8000-00aa00389b71
        bits per pixel: 32
        number of planes: 1
        type: RGB (packed)
        depth: 32
        red, green, blue masks: 0xff0000, 0xff00, 0xff
      id: 0x0
        guid: 52474200-0000-0010-8000-00aa00389b71
        bits per pixel: 24
        number of planes: 1
        type: RGB (packed)
        depth: 24
        red, green, blue masks: 0xff0000, 0xff00, 0xff
      id: 0x54424752 (RGBT)
        guid: 52474254-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: RGB (packed)
        depth: 16
        red, green, blue masks: 0x7c00, 0x3e0, 0x1f
      id: 0x32424752 (RGB2)
        guid: 52474200-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: RGB (packed)
        depth: 16
        red, green, blue masks: 0xf800, 0x7e0, 0x1f
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
```



Any idea ?

J.L.

---

### Post by misiu_mp on 2006-11-29
I have exactly the same problem with my radeon 9100 card.
I got the drm and dri to work so i can use opengl overlay for movies but the xv driver just shows a rectangle coloured by the YUV video overlay key color.

It looks just like described above.

I need help with this.

---

### Post by misiu_mp on 2006-12-01
Anyone have an idea why would xv hardware overlay be broken for the radeon driver? Im starting to get desperate.

---

### Post by CarpKing on 2006-12-02
Not sure if it's relevant or not, but this is suspiciously similar a problem I have with Xv output and the free radeon driver.  My problem only shows up when I'm using Beryl, though, and the output only turns black when another object (window, popup, etc) passes in front of the video.  I have an ATI 9600.

---

### Post by misiu_mp on 2006-12-02
The problem could have same root but is quite different.
I get a black window (or blue or green or whatever overlay key color I choose) at all times in all apps using the xv driver (tried with mplayer, vlc and xine).

---

### Post by OntzA on 2006-12-29
I registered in this forum just to answer this question.

It has taken me a lot of googling and reading posts in forums to get the solution to this problem. I also have a Radeon 9100 and xv output didn't work until I added this lines to the driver section:

```
Option "MergedXinerama" "false"
Option "MergedFB" "false"
```

I got those lines from [this post]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/38181/comments/24").

The Xorg docs say MergedFB allows to share a frame buffer and you can choose where de xvideo overlay goes between the two monitor, I guess this doesn't work right with the Radeon 9100.


Now i'm really happy with my Ubuntu desktop, I can watch videos and play Quake 3 without any problems.

---

### Post by misiu_mp on 2007-01-04
Thanks so very much man!
That was it.
Pitty the dual wont work. Maybe it is as simple as moving the overlay output to the right screen.

---

