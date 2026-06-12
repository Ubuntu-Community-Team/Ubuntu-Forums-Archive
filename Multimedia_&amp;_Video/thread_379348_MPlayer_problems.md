---
title: "MPlayer problems"
date: 2007-03-08
forum: Multimedia &amp; Video
---

### Post by NaCl on 2007-03-08
I have 1280x1080 video file that I cannot play. I have the required codecs installed. When I try to play it using command line, it returns
bash: syntax error near unexpected token `('
I first suspect it'd be caused by beryl, so when I logged on to the GNOME session (no beryl). Didn't work.
I also tried VLC and Totem. Didn't work.
I can play the file perfectly file on Windows using the same computer.

Could the reason be that the file is too large and its resolution than my desktop resolution?

I also have another problem. I notice that when I was playing some divx3, OSDs break into pieces as the frames changes.

---

### Post by panch0 on 2007-03-09
The bash error probably means it's trying to interpret the file name as a complex command.

To prevent that enclose the file name in single quotes like this:

mplayer 'file.avi'

---

### Post by NaCl on 2007-03-10
the error is gone, and i managed to play the file with x11
but then the resolution is too big

the file's resolution exceeds my desktop's resolution
is there a way to play it as whole, llike everything is within the screen
i was able to play the video in x11

---

### Post by panch0 on 2007-03-12
MPlayer has a -zoom option, so try playing like

mplayer -zoom movie.avi

It's good that you can play it with x11, but you should really try to use XVideo, it saves you a lot of resources on your computer. What happens if you try this:

mplayer -zoom -vo xv movie.avi

---

### Post by NaCl on 2007-03-13
My default playing mode is in xv. Nope, the video doesn't play in xv.
This is the output
AVI file format detected.
VIDEO:  [XVID]  1280x1080  16bpp  29.970 fps  4652.1 kbps (567.9 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 256.0 kbit/16.67% (ratio: 32000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 1280 x 1080 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1280x1080 => 1920x1080 Planar YV12  [zoom]
aspect: Warning: no suitable new res found!
aspect: Warning: no suitable new res found!
aspect: Warning: no suitable new res found!
aspect: Warning: no suitable new res found!
[mpeg4 @ 0x88a5b38]frame skip 8t:  0.000   1/  1 ??% ??% ??,?% 0 0 
[mpeg4 @ 0x88a5b38]frame skip 8t:  0.000   2/  2 ??% ??% ??,?% 1 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 3 0 


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

I have 1GB of ram.

---

### Post by panch0 on 2007-03-14
What does xvinfo say?

---

### Post by NaCl on 2007-03-14
This is the outpout
> X-Video Extension version 2.2
screen #0
  Adaptor #0: "Intel(R) Video Overlay"
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
    number of attributes: 10
      "XV_COLORKEY" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 66046)
      "XV_BRIGHTNESS" (range -128 to 127)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_CONTRAST" (range 0 to 255)
              client settable attribute
              client gettable attribute (current value is 64)
      "XV_DOUBLE_BUFFER" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_GAMMA0" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 526344)
      "XV_GAMMA1" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 1052688)
      "XV_GAMMA2" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 2105376)
      "XV_GAMMA3" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 4210752)
      "XV_GAMMA4" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 8421504)
      "XV_GAMMA5" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 12632256)
    maximum XvImage size: 1920 x 1080
    Number of image formats: 4
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
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
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
  Adaptor #1: "Intel(R) Textured Video"
    number of ports: 16
    port base: 74
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
    number of attributes: 2
      "XV_BRIGHTNESS" (range -128 to 127)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_CONTRAST" (range 0 to 255)
              client settable attribute
              client gettable attribute (current value is 0)
    maximum XvImage size: 2048 x 2048
    Number of image formats: 4
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
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
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)


---

### Post by panch0 on 2007-03-15
What is your MPlayer version? It reports the version in the first line of its output, but in your cut and paste it got cut off.

---

### Post by NaCl on 2007-03-16
MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team

I compiled it following [http://ubuntuforums.org/showthread.php?t=336706&highlight=mplayer+source](http://ubuntuforums.org/showthread.php?t=336706&highlight=mplayer+source)

I put the codecs in the correct folder /usr/local/lib/codecs
and just a simple 
./configure --enable-gui --disable-mp3lib

I can play other files fine. Although I am experiencing a little problem with OSD when playing some files.

---

### Post by panch0 on 2007-03-16
To tell you the truth I don't see anything wrong with your setup, and your MPlayer is current. So maybe report a bug on the [mplayer-users list]("http://www.mplayerhq.hu/design7/mailing_lists.html") and include the MPlayer output with -v option. At the very least they should fix it so that it gives a meaningful error and doesn't crash.

---

### Post by NaCl on 2007-03-17
Thank you for helping me panch0

---

