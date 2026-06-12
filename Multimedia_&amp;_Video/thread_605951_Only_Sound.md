---
title: "Only Sound"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by boofoohacker on 2007-11-07
This problem starting happening after I upgraded from Ubuntu 7.04 to 7.10 about 3 days ago. Now whenever I open a video in totem and all other media players available, I can hear sound, but the video is not shown correctly. The video shows the color of the actual frame of the video, but it only shows the color in vertical lines. I attempted to take a screenshot of the problem in totem, but weirdly unlike what I'm seeing it actual shows the video frame correctly.

---

### Post by trak87 on 2007-11-07
Maybe dump totem and use mplayer instead. It's the most capable media player.

---

### Post by boofoohacker on 2007-11-07
When I try MPlayer it gives me an error as shown in the screenshot below

---

### Post by trak87 on 2007-11-07
You're missing one or more codec packages. You might search synaptic on the word 'codec' see what comes up. What kind of file are your trying to view?  Run mplayer from the command line (mplayer <filename>)and see what kind of video it detects in the information given on screen. That may help you in determinine what to install. There are other repositories you may need to enable as well.

---

### Post by boofoohacker on 2007-11-08
Here is the output from mplayer command line

>  mplayer /home/*private*/Videos/use_multiple_workspaces.ogg
MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Celeron(R) D CPU 3.20GHz (Family: 15, Model: 6, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/*private*/Videos/use_multiple_workspaces.ogg.
[Ogg] stream 0: video (Theora v3.2.0), -vid 0
[Ogg] stream 1: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [theo]  642x482  24bpp  9.000 fps    0.0 kbps ( 0.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x88a96d8]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 642 x 482 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 642x482 => 642x482 Planar YV12 
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 499.8 kbit/35.42% (ratio: 62477->176400)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis decoder)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
No bind found for key 'MOUSE_BTN0'.                         ?% 0 0 
gnome_screensaver_control()11 ct:  0.016  20/ 20  3%  5%  4.0% 0 0 
Exiting... (Quit)


---

### Post by boofoohacker on 2007-11-09
Bump

Please I really need help

---

### Post by trak87 on 2007-11-09
At the bottom of the following page they show how to download and install the w32codecs package:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

To summarize, open a terminal and run (by cutting and pasting of course) the following:
```
wget -c http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20061022-0medibuntu1+build1_i386.deb
sudo dpkg -i w32codecs_20061022-0medibuntu1+build1_i386.deb

```

Now try running mplayer with your .ogg file.

BTW, is this .ogg file on the net somewhere where anybody can download it?

---

### Post by trak87 on 2007-11-09
Another thing you could try:

mplayer -vo <videodriver> filename.ogg

Where in place of <videodriver> you type one of these: xv, x11, gl, gl2, sdl, vesa

If that doesn't work, open up Synaptic and see if you have the following installed. If not, install them (based on this message: [http://lists.mplayerhq.hu/pipermail/mplayer-users/2007-May/067304.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2007-May/067304.html)) :

libtheora0
libvorbis0a
libvorbisenc2
libvorbisfile3

---

### Post by boofoohacker on 2007-11-12
I don't know what I did, but I have managed to get it to work. Instead of creating a new topic I will just ask in this one quickly. Is there any media players that can play wvx files from within firefox?

---

